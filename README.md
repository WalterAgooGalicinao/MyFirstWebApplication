<p align="center"> <img width="30%" src="https://dev.inchcape.digital/media/0-images/navigation/Inchcape_Digital_Logo_Hor_rgb-1.png" alt="Inchcape Digital Logo"> </p>
<p align="center">A CMS Umbraco Project for Inchcape Digital</p>
<p align="center">
<a href="https://dev.inchcape.digital/">
<img alt="Development Deployment" src="https://img.shields.io/badge/development_deployment-%E2%9C%94-green?style=for-the-badge" />
</a>
 <a href="https://qa.inchcape.digital/">
<img alt="QA Deployment" src="https://img.shields.io/badge/qa_deployment-%E2%9C%94-green?style=for-the-badge" />
</a>
<a href="">
<img alt="Production Deployment" src="https://img.shields.io/badge/production_deployment-%E2%9C%98-red?style=for-the-badge" />
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
These deployment status will show up once deployment has been triggered and can be seen beside the latest commit that have been made. 

### For reference:
```bash
Deployment Ongoing - •
Deployment Done - ✓
```

## Author

- [@WalterAgooGalicinao](https://github.com/WalterAgooGalicinao)

