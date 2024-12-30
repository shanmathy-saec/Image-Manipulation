def encrypt_decrypt_image(path, key):
    try:
        with open(path, 'rb') as fin:
            image = fin.read()
        
        
        image = bytearray(image)
        for i in range(len(image)):
            image[i] ^= key  

        
        with open(path, 'wb') as fout:
            fout.write(image)
        
        print('Encryption/Decryption done successfully!')
    
    except FileNotFoundError:
        print(f"Error: File '{path}' not found. Please check the file path.")
    except ValueError:
        print("Error: The key must be a valid integer.")
    except Exception as e:
        print(f"An error occurred: {e}")


def main():
    
    path = input('Enter the path of the image: ').strip()
    key = input('Enter the encryption key (an integer): ').strip()

   
    try:
        key = int(key)
    except ValueError:
        print("Error: The key must be a valid integer.")
        return

   
    path = path.replace("\\", "/")  
    print(f"File path: {path}")
    print(f"Encryption/Decryption key: {key}")

    
    encrypt_decrypt_image(path, key)


if __name__ == "__main__":
    main()
