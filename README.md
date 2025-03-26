# Python_week4-challenge
#python 3.7.1

def modify_and_write_file(input_filename, output_filename):
    """
    Reads a file, modifies its contents, and writes to a new file.

    Args:
        input_filename: The name of the input file.
        output_filename: The name of the output file.
    """
    try:
        with open(input_filename, 'r') as infile, open(output_filename, 'w') as outfile:
            for line in infile:
                # Example modification: Uppercase each line
                modified_line = line.upper()
                outfile.write(modified_line)
        print(f"File '{input_filename}' successfully modified and written to '{output_filename}'.")

    except FileNotFoundError:
        print(f"Error: File '{input_filename}' not found.")
    except IOError:
        print(f"Error: Could not read or write to the file.")
    except Exception as e:
        print(f"An unexpected error occurred: {e}")


def get_filename_and_process():
    """
    Asks the user for a filename and handles potential errors during file reading.
    """
    while True: # loop until valid filename is entered.
        filename = input("Enter the filename to read: ")
        try:
            with open(filename, 'r') as file:
                # Read the file and do something with the content (e.g., print it)
                print(f"Contents of '{filename}':")
                print(file.read())
                break # break out of the loop if file is read successfully.

        except FileNotFoundError:
            print(f"Error: File '{filename}' not found. Please try again.")

        except IOError:
            print(f"Error: Could not read '{filename}'. Please check file permissions or if the file is open in another application. Try again.")

        except Exception as e:
            print(f"An unexpected error occurred: {e}. Please try again.")

# Example usage:
input_file = "input.txt"  # Create this file with some text
output_file = "output.txt"

#Create a test input file if it does not exist.
try:
  with open(input_file, "x") as f:
    f.write("hello world\nthis is a test\n")
except FileExistsError:
  pass #do nothing if file already exists.
modify_and_write_file(input_file, output_file)

get_filename_and_process()
