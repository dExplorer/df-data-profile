# df-data-profile

### Install

- **Install via setuptools**:
  ```sh
    python setup.py install
  ```


### Usage Examples

- **Profile a dataset via CLI**:
  ```sh
    dp_app profile-dataset --dataset_id "3" --env "dev"
  ```

  ##### If not installed
  ```sh
    python dp_app profile-dataset --dataset_id "3" --env "dev"
  ```

- **Profile a dataset via API**:
  ##### Start the API server
  ```sh
    python dp_app/dp_app_api.py
  ```
  ##### Invoke the API endpoint
  ```sh
    https://<host name with port number>/profile-dataset/{dataset_id}
    https://<host name with port number>/profile-dataset/3
  ```
  ##### Invoke the API from Swagger Docs interface
  ```sh
    https://<host name with port number>/docs

    /profile-dataset/{dataset_id}
    /profile-dataset/2
  ```

### Sample Input

```
first_name,last_name,full_name,ssn,dob,street_addr1,street_addr2,city,state,country
John,Connor,John Connor,987-65-4321,1988-05-03,155 North Blvd,,New York City,NY,USA
Jill,Valentine,Jill Valentine,123-45-6789,1990-06-25,155 North Blvd,,Los Angeles,CA,USA
```

### Sample Output 

```
[
    {'column_name': 'first_name', 'info_type': 'NAME', 'data_class': 'PII'}, 
    {'column_name': 'last_name', 'info_type': '', 'data_class': 'NON PII'}, 
    {'column_name': 'full_name', 'info_type': 'NAME', 'data_class': 'PII'}, 
    {'column_name': 'ssn', 'info_type': 'SSN', 'data_class': 'PII'}, 
    {'column_name': 'dob', 'info_type': 'DATE OF BIRTH', 'data_class': 'PII'}, 
    {'column_name': 'street_addr1', 'info_type': 'ADDRESS', 'data_class': 'PII'}, 
    {'column_name': 'street_addr2', 'info_type': '', 'data_class': 'NON PII'}, 
    {'column_name': 'city', 'info_type': 'GPE', 'data_class': 'NON PII'}, 
    {'column_name': 'state', 'info_type': 'ORG', 'data_class': 'NON PII'}, 
    {'column_name': 'country', 'info_type': 'GPE', 'data_class': 'NON PII'}, 
    {'column_name': 'last_name', 'info_type': 'NAME', 'data_class': 'PII'}
]
```