# Basic Linux Command Line

I gathered some command line to work on Linux that I ended up using every day as a data analyst.

1. delete a file:

    `rm FILE_NAME`

2. Delete a directory and its content:

    `rm -r DIRECTORY_NAME`

3. Move a file:

    `mv SOURCE_DIRECTORY_PATH/FILE_TO_BE_REMOVED DIRECTORY_WHERE_YOU_WANT_TO_MOVE_THE_FILE/`

    If you already are in the directory where the file is, then:

    `mv FILE_NAME DIRECTORY_WHERE_YOU_WANT_TO_MOVE_THE_FILE`

4. To see the content of a file wihtout open it:

    `cat filename.txt`

5. To visualize the beginning of a file content:

    `head myfile.txt`

6. To visualize the end of a file content:

    `tail myfile.csv`

7. To list files and directories you can use:

    `ls`

    Sometimes you also need to see hidden files and directories:

    `ls -la`

8. To copy the content from um file to another:

    `cp copyfromhere.txt copied.txt`

9. To move a file:

    `mv myfile.txt movefilehere/`

10. To unzip: 

    `tar -xzf itiscompacted.tar.gz`
