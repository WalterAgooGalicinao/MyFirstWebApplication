<p align="center"> <img width="30%" src="https://dev.inchcape.digital/media/0-images/navigation/Inchcape_Digital_Logo_Hor_rgb-1.png" alt="Inchcape Digital Logo"> </p>
<p align="center">A CMS Umbraco Project for Inchcape Digital</p>
<p align="center">
<a href="https://dev.inchcape.digital/">
<img src="https://img.shields.io/badge/development_deployment-%E2%9C%94-green?style=for-the-badge" alt="Development Deployment"/>
</a>
 <a href="https://qa.inchcape.digital/">
<img src="https://img.shields.io/badge/qa_deployment-%E2%9C%94-green?style=for-the-badge" alt="QA Deployment"/>
</a>
<a href="">
<img src="https://img.shields.io/badge/production_deployment-%E2%9C%98-red?style=for-the-badge" alt="Production Deployment"/>
</a>
</p>

## Deployment
To trigger the deployment please make sure to retain the following files and their code before pushing to the branch, creating a pull request, and merging.

#### Program.cs
```bash
namespace inchcape_digital
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
        "Id": "6ca9ecd7-15d6-427c-b999-05da837ca058",
        "SanitizeTinyMce": true
      },
      "Content": {
        "ContentVersionCleanupPolicy": {
          "EnableCleanup": true
        }
      }
    }
  },
  "ConnectionStrings": {
    "umbracoDbDSN": "",
    "umbracoDbDSN_ProviderName": "Microsoft.Data.SqlClient"
  }
}
```

## Deployment Status
The deployment status will appear once the deployment has been triggered and can be viewed next to the latest commit that has been made. 

```bash
Deployment Ongoing - ⦿
Deployment Done - ✔
```

## Author
- [@WalterAgooGalicinao](https://github.com/WalterAgooGalicinao)

## License
This project is licensed under Inchcape.
<p>
<a href="https://www.inchcape.com/">
<img src="https://img.shields.io/badge/license-inchcape-blue?style=for-the-badge" alt="Inchcape"/>
</a>
</p>
