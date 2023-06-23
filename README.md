
<p align="center"> <img src="https://dev.mercedes-benz.ph/media/qbfh3px4/mb-star-svgsvg.png" alt="Mercedes-Benz Logo"> </p>


<h1 align="center"> Mercedes-Benz Philippines </h1>

<p align="center"> A CMS Umbraco Project for Mercedes-Benz Philippines. </p>


## Deployment

Before creating a pull request and merging, please retain the following files and its code

#### Program.cs
```bash
namespace MB_PH
{
    public class Program
    {
        public static void Main(string[] args)
            => CreateHostBuilder(args)
                .Build()
                .Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureUmbracoDefaults()
                .ConfigureHostConfiguration(config =>
                {
                    config.AddEnvironmentVariables("ASPNETCORE_");
                })
                .ConfigureAppConfiguration((hostingContext, config) =>
                {
                    config.AddEnvironmentVariables("ASPNETCORE_");
                })
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseStaticWebAssets();
                    webBuilder.UseStartup<Startup>();
                });
    }
}
```
#### appsettings.json
```bash
{
  "Captcha": {
    "SecretKey": "6LfvM2IjAAAAAOn7TkMLOoy4duZRQZ8rQfWU9XKb"
  },
  "$schema": "./appsettings-schema.json",
  "Serilog": {
    "MinimumLevel": {
      "Default": "Information",
      "Override": {
        "Microsoft": "Warning",
        "Microsoft.Hosting.Lifetime": "Information",
        "System": "Warning"
      }
    }
  },
  "Umbraco": {
    "CMS": {
      "Global": {
        "Smtp": {
          "From": "development-testing@ddcfrontdoordev.ml",
          "Host": "smtp.sendgrid.net",
          "Port": 587,
          "DeliveryMethod": "Network",
          "enableSsl": true,
          "Username": "",
          "Password": "",
          "SecureSocketOptions": "StartTls"
        },
        "Id": "228f3fba-f6cd-4f91-aa55-f79358b69678",
        "SanitizeTinyMce": true
      },
      "Content": {
        "AllowEditInvariantFromNonDefault": true,
        "ContentVersionCleanupPolicy": {
          "EnableCleanup": true
        },
        "Error404Collection": [
          {
            "Culture":"default",
            "ContentKey": "5f004a7a-3bbb-4ad3-8091-e64ec20b8513"
          }
        ]


      }
    }
  },

  "ConnectionStrings": {
    "umbracoDbDSN": "",
    "umbracoDbDSN_ProviderName": "Microsoft.Data.SqlClient"
  }
}
```

## Authors

- [@WalterAgooGalicinao](https://github.com/WalterAgooGalicinao)

