
<p align="center">
    <img src="https://dev.mercedes-benz.ph/media/qbfh3px4/mb-star-svgsvg.png" alt="Mercedes-Benz Logo">
</p>


<h1 align="center"> Mercedes-Benz Philippines </h1>

A CMS Umbraco Project for Mercedes-Benz Philippines.


## Deployment

Before creating a pull request and merging, please retain the following files and its code

```bash
// Program.cs
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


## Authors

- [@WalterAgooGalicinao](https://github.com/WalterAgooGalicinao)


## Optimizations

What optimizations did you make in your code? E.g. refactors, performance improvements, accessibility

