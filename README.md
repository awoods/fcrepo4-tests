# Fedora 4 Tests

These shell scripts are meant to be run against a standalone Fedora 4 instance. 

This will create, update and delete resources in the repository. So you may **not** want to use it on a production instance.

Also, this is doing a cursory test. It relies on the response from Fedora and does not verify changes to the RDF.

## Usage

Edit the `config` file and review the default variables to ensure the tests are pointing at your repository. 

Run each/all/any of the test scripts.

## Tests implemented

### nested\_test.sh
1. Create a container
2. Create a container inside the container from step 1
3. Create a binary inside the container from step 2
4. Delete the binary
5. Delete the container from step 1

### fixity\_test.sh
1. Create a binary resource
2. Get a fixity result for that resource

### sparql\_tests.sh
1. Create a container
2. Set the dc:title of the container with a Patch request
3. Update the dc:title of the container with a Patch request
4. Create a binary
2. Set the dc:title of the binary with a Patch request
3. Update the dc:title of the binary with a Patch request

### transaction\_tests.sh
1. Create a transaction
2. Get the status of the transaction
3. Create a container in the transaction
4. Verify the container is available in the transaction
5. Verify the container is **not** available outside the transaction
6. Commit the transaction
7. Verify the container is now available outside the transaction
8. Create a second transaction
3. Create a container in the transaction
4. Verify the container is available in the transaction
5. Verify the container is **not** available outside the transaction
6. Rollback the transaction
7. Verify the container is still **not** available outside the transaction
 