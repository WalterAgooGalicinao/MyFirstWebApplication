
# Mercedes-Benz Philippines

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


<p align="center">
    <img width="200" src="http://material-bread.org/logo-shadow.svg" alt="Material Bread logo">
</p>

