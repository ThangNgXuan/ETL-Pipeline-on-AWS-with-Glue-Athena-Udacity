# Build the ETL process with AWS Glue and AWS Athena on AWS

## Project Scope

- Store the raw data in **S3 bucket** as a Landing Zone.
- Create the data catalog applying the schema for each table in the Landing Zone using **Glue Catalog**.
- Create **Glub Jobs** that processes or transforms the data including to filter, exclude null, and join data. Then, move the cleaned data into **S3 bucket** as a Trusted or Curated Zone.
- Use **Athena** in order to query data in the **Glue tables** and implement some of anylytics purposes.

### Getting Started

- Create IAM Role for AWS Glue and S3 access to other services.
- Copy data from external source into S3 Bucket as a Landing Zone.
    ```
    aws s3 cp ./project/starter/accelerometer/ s3://springwin/accelerometer/ --recursive
    ```

### Project instruction

- Create 2 **Glue tables** for customer_landing and accelerometer_landing. Then use **Athena** to test the queries running.
- Create 2 **Glue Jobs** for customer_landing_to_trusted and accelerometer_landing_to_trusted filtering people who agreed to share their data. 
- Create 2 **Glue tables** for customer_trusted and accelerometer_trusted. Then use **Athena** to test the queries running.
- Create 1 **Glue Job** for customer_trusted_curated including only customer email.
- Create 1 **Glue table** for customer_curated. Then use **Athena** to test the queries running.
- Create 1 **Glue Job** for step_trainer_trusted joining customer_curated and step_trainer_landing.
- Create 1 **Glue Job** for machine_learning_curated joining step_trainer_trusted and accelerometer_trusted.

### AWS Architecture
# Project Workflow ([link](https://viewer.diagrams.net/index.html?tags=%7B%7D&highlight=0000ff&edit=_blank&layers=1&nav=1&title=aws_glue_athena_project.drawio#R7V1tc5s4EP41%2BRgGId780XaStjftXNr0ptf7kiFYsWkwckFu4vv1J%2FFmQIuNG7BxjrQzMSuZF%2B2zq9WzK3KBp8uXd6GzWnyiM%2BJfaOrs5QJfXWgaMm2L%2FxKSTSIZYTMRzENvlnbaCu68f0kqVFPp2puRqNSRUeozb1UWujQIiMtKMicM6XO52yP1y1ddOXMiCe5cx5el37wZWyRS21C38vfEmy%2ByKyM1bXlw3Kd5SNdBer2ABiRpWTrZadKu0cKZ0eeCCF9f4GlIKUs%2BLV%2BmxBfDmo1Y8r2bmtb8lkMSsCZfeP%2FP3ZO3njz%2FNL483rr08%2FTH981lpoBfjr9OxyK9W7bJBmfBlj7%2FhC7w5BcJmceH7aPzQPxbGnnMowFve6CM0SXv4PjeXAhcflMk5AJf9JzkozSlPg3j0%2BLH%2BKdw0nH6XUZXXBqxkD7l2tBySeEMqmqrN6poyYZW3OPMiRZEPHPashKPsXyZC%2BQqHo0sxeMwipSZwxzeQx7GdGTFbZGXgigd1neELgkLN7xL1qqno5iiH2NN0VIDeN7CyTQVIxEuCliyjEzqpCCe5xfYapN%2FSBV6iHIRoFzTZ2JcVk5Q0rL5cy2AOHmkAbuMYgMd8w7IXL3Eg5S1809z8fuL8yzsXYxhekp%2Bi8lZkw4SjPhgCnkBTWWFxqbDb8Dz%2FYooA5VPHhmAl6U3m4mLTJ4XHiN3K8cVV3zm%2BuayGHU5HNpQNs4Vlql7ZCsGktRtIVnZutaVqrE03jRkCzqnAbdWKiwqHvIfhLFN6n%2BdNaNlhfBRCTd%2Fi7FSNCM7%2Fp6OXXxw9VI62qRH5VF%2B9OnzOPC4B0y8gzj19m7yE6yXJHQY2VpqYsOqZPx4l%2BYiug5d0sDFMSecE7ajYzqEZFaaK2QghMTnT%2FarPHW8RqP29PJ2%2FedP%2FeN7dH357dON%2Bfnv8aUm2e742x0XTH26nknKXlEvYPEtGBP%2Bnz%2FyVL0weMtUHAltlgXVY6ssQPKROEdZUD22ygJUPT2qXB9Vb7AgkI5Kp1cr11cLN8j%2Fc7Stme8F3LVk4YIAFZ8BZh6HT8W7FPAPORDhEFODQVp2nA68OCufS5jDrxWm54g1QcLrXyRRSNLH951V5D3k3wqJuw4jDqIvJHG24GzlPEe6IibOVXz7H9zYnOTWe%2F7x3hXAuHcS916dKvm%2FGwE%2ByL3C82%2FF6XLX7nrB%2FGN8dIXVdCSgS5Qm4Br3CphyrcflXjPGR8HloiyoKvhbhDUrBlrV6eIsjGvfRkeSIZY94e%2F44BePJS7YSI%2B%2BF1q2%2FlccZO634LcPctugwyurZpdvKrpeuJ8lu16wIzJP6mqt%2FUHwVq91jqIY2BTj0UYWUD%2FMtWZhYJTDPYtEAKswDcUeyUaRr2BaH01TDkUEwjKfuTWJ66108nqzyU2gZABbe6gxATnSgKKXrg0FmQ0NpbByPIGhZLd5Zoai64pVnj5sQ8E2MINYigpMIPls0%2FqAjs5xPMXytuJ4oOnYVI85ksg4idcBJ%2Bt8ft43WeORVfRWaI%2Bvio9uSejxIYvjzf44ML2h%2F7JP6r7sU2IEFRGS42UfRs5xNmsKhtNGffob8b11k1ln%2FhckTxrMZNETYe4iRSpIWICkBURcgOSFTGCUusWUAnCFqhCSWbIQyd0yFkIWQjKIcql%2BGwHfRpVv1xMedQv0KhHC20a6cXWjFdquvJCfKPEZgfB6Fe6Af8cYY3ViQGxDTu2XqIC9yYPdRESeUijY3D5yxolWyXA8ei%2FiPmCGJSSJS0v4lQk%2FhJgWhy1IAGcMdhJ4jZllbFtV2zbkuAoya%2FNwq%2F4rIuGfDz%2FE6GhqnKQpWm2afEtE74RJa%2BrUYY5P50mHnb7AKjxm6jvq3MCrcAtkDHh3%2FUqzxmMJlmnn3iGyyheiWh6Qq%2BFeJFzu3VQT4JzTAS4NIN7fsgr7sKkro9HB8OSHBYQekgiBpvWWcl7ZiR4yQdUyTGcp8BE8RKtCd%2F4sD9VTnGeyrCU8AetHE4MxjGrKgGojhwY%2BiMwCfnUEY78zjmnDgTVj69%2FqvMriQe4uZNaxLcENgXAzAPfVWe7APqKfGiehy5vwRx2sqeS4CyEg8MIyOnBndNZpSPQjUhUQMVGX9m%2BFqoDDhYtmVIUOI6h1pmLXTXbJVHQwy8tGBRMVmt4SUXHAkuaOm5c6Wbt8Jm%2Bwnim6jz3rmYHW6BWtYapjjK3DaA3NshAy%2Fze0RgRXV7XjBEzJCXCdQE6gJVbjt5eNuDYaE2PfbjQmnM%2FOSCy5ZGeRWI64Hq4NNRkwBlIMqxFg2ojGQHTUcwqvRoe7jriXIKHyI6JBDpUwa44YWd2zMC4wq%2BniuC7xSUjjpGCpT%2FdQ6i%2FJgOT4Q8MIJBk0AEpWV1AyaqG0QJmiPjrBzAvmvNs%2F8XaCXJvbLi3qMq3s4wJje%2FQ1XjGIchNYiZRrQkTwXLLgyibB0RRr6VJcOYL1OgL0qne2YNMaKPZQr6FpNV7j89pzn8Rj8NXdJvKiWos%2FY%2BicrHClK9yA%2FgCigXbxjcMCo1cLjCFvuneBMY%2BR3dl8YJhSdd%2FIVCxg%2B5WuZBuiKvmpTNz%2BpAAVFnecjPqDPhSng4HpLWLFqGJFM2xFlxOZx0086TLZe1ZUbj%2BqzrKpfC%2BXi49F5oJXN7rYM1K3b29fRemZac6oMe8jbRNpsFe6fxWDFlAxyNdQJuD0wIpBfbu4On55Efy8xYBgqC86cn1RBwgF6ouQqRjWaPvTkDHurNYIfqz6Nf9Qa9SPiA%2FwfoJBUmVC%2BbghnyYnHIZiozdQbGQDxUYaiLejFhtpDTY7DDRTf2mmG0O3%2BDL1IJppaiGMbv43NJM34zfgsc29E8zuRU4siu6XTuDMyTI26A63l2qKYRdilZL16zLBbCJwl2lB3L7916ed2o9UPow%2F8f5fqJjNhiil2VZ%2BnJOQ2RpNFXBQtz%2FyC4ZsYAbpbH%2Bt1mG9agkwlex2XKl1S33P9TZyaxoUx%2B1A84At4VYkbOmGhCUo59VGDhwm4CAipZor%2FRquI8ZH5w0kwbtY1uiSw7BscFlj2IqpAyubzpTb4UvnbjxfxBg1s8rW7q8Kr6UbvEHJG%2FD1SQU4fKqByiegqtzOPELmkd5uuXs%2FmHbcdGs%2BPumLGvBZ7s0f6Y335h%2F9RTMYWgAMBMDZEABDnclhdSYdWLcpW3dvCk0w9GKuodDkZGHWCEhp9aHSxESSGtosPsCWWYyKBIOxLy7q8Tutsol7f1nCSd9jhBuUkPYvWEJI3upx5nUJeFR44qEu4ezrEhDS5T0kZ1GYoNcTbENhQj8iBMj%2F9aIyQZf5u6Ey4Q1UJiAN4z6WJmRA3pkMmK7FX4qYDcmA5qEUnA2wjp0N6HAHxB88gniL3H9IWbbM6RQ2qmYqtillmPOdcdw3mIVIR5fQdNQUgQHFNL1f5li6WvlrQad%2FVbYhz%2FC7J%2FeBCx644PMKpirvau3ArkfVvwLW3ataG1p1fRw1vFDuyEXnEjhO%2Fj45o%2F4FN8PrCXoSxzeLFY76VgvjLBPxILdy%2BrBrSMEPYdcQdr3Ssm0psXrywOuYufch8DoUHqcPveopsCH06kno1TRiaCn44ofbv%2Fset70TTvQTnYl89PV%2F) to draw.io)
<img src="result_image\aws_architecture.gif" class="img-responsive" alt=""> </div>
