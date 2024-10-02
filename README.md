# Aspire Dashboard

## 簡単起動

```bash
docker run --rm -it -p 18888:18888 -p 4317:18889 -d --name aspire-dashboard mcr.microsoft.com/dotnet/aspire-dashboard:latest
```

## webapiをトレース

```bash
dotnet workload update
dotnet workload install aspire
```

## Blazor ServerにAspireを導入する

おおまかな流れ

- appsettings.Development.jsonに環境変数を追加する
- BlazorApp.csprojを修正する
- Extensions.csを追加する
- Program.csにAddServiceDefaultsとMapDefaultEndpointsを追加する

## appsettings.Development.jsonに環境変数を追加する

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "OTEL_EXPORTER_OTLP_ENDPOINT": "http://localhost:4317",
  "OTEL_SERVICE_NAME": "BlazorServer"
}
```

## なんか動かないなと思ったら

GitHub Codespacesで動かしているときに動かないと思ったらTrusted Domainやプロトコル、公開の状態をみると良い。
