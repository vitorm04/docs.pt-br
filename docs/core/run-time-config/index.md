---
title: Opções de configuração de tempo de execução
description: Saiba como configurar aplicativos .NET Core usando configurações de configuração em tempo de execução.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399157"
---
# <a name="net-core-run-time-configuration-settings"></a>Configurações de configuração de tempo de execução do .NET Core

O .NET Core suporta o uso de arquivos de configuração e variáveis de ambiente para configurar o comportamento de aplicativos .NET Core em tempo de execução. A configuração em tempo de execução é uma opção atraente se:

- Você não possui ou controla o código-fonte de um aplicativo e, portanto, não consegue configurá-lo programáticamente.

- Várias instâncias do aplicativo são executadas ao mesmo tempo em um único sistema, e você deseja configurar cada uma para um desempenho ideal.

> [!NOTE]
> Esta documentação é um trabalho em andamento. Se você notar que as informações aqui apresentadas são incompletas ou imprecisas, [abra um problema](https://github.com/dotnet/docs/issues) para nos informar sobre isso ou envie uma solicitação de [retirada](https://github.com/dotnet/docs/pulls) para resolver o problema. Para obter informações sobre o envio de solicitações de retirada para o repositório dotnet/docs, consulte o [guia do contribuinte](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).

O .NET Core fornece os seguintes mecanismos para configurar o comportamento do aplicativo em tempo de execução:

- O [arquivo runtimeconfig.json](#runtimeconfigjson)

- [Propriedades do MSBuild](#msbuild-properties)

- [Variáveis ambientais](#environment-variables)

Alguns valores de configuração também <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> podem ser definidos programáticamente chamando o método.

Os artigos desta seção da documentação são organizados por categoria, por exemplo, [depuração](debugging-profiling.md) e [coleta de lixo.](garbage-collector.md) Quando aplicável, as opções de configuração são mostradas para arquivos *runtimeconfig.json,* propriedades MSBuild, variáveis de ambiente e, para cross-reference, *app.config* files para projetos .NET Framework.

## <a name="runtimeconfigjson"></a>runtimeconfig.json

Quando um projeto é [construído,](../tools/dotnet-build.md)um arquivo *[appname].runtimeconfig.json* é gerado no diretório de saída. Se um arquivo *runtimeconfig.template.json* existir na mesma pasta que o arquivo do projeto, todas as opções de configuração que ele contém serão mescladas no arquivo *[appname].runtimeconfig.json.* Se você estiver construindo o aplicativo você mesmo, coloque quaisquer opções de configuração no arquivo *runtimeconfig.template.json.* Se você estiver apenas executando o aplicativo, insira-os diretamente no arquivo *[appname].runtimeconfig.json.*

> [!NOTE]
> O arquivo *[appname].runtimeconfig.json* será substituído em compilações subseqüentes.

Especifique opções de configuração em tempo de execução na seção **configPropriedades** dos arquivos *runtimeconfig.json.* Esta seção tem o formulário:

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Exemplo [appname].runtimeconfig.json

Se você estiver colocando as opções no arquivo JSON de saída, aninham-as a `runtimeOptions` propriedade.

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a>Exemplo de runtimeconfig.template.json file

Se você estiver colocando as opções no arquivo JSON do modelo, omita a `runtimeOptions` propriedade.

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a>propriedades MSBuild

Algumas opções de configuração em tempo de execução podem ser definidas usando propriedades MSBuild no arquivo *.csproj* ou *.vbproj* de projetos .NET Core no estilo SDK. As propriedades mSBuild têm precedência sobre as opções definidas no arquivo *runtimeconfig.template.json.* Eles também sobreescrevem todas as opções definidas no arquivo *[appname].runtimeconfig.json* no momento da compilação.

Aqui está um exemplo de arquivo de projeto no estilo SDK com propriedades MSBuild para configurar o comportamento em tempo de execução:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

As propriedades do MSBuild para configurar o comportamento em tempo de execução são observadas nos artigos individuais para cada área, por exemplo, [coleta de lixo](garbage-collector.md).

## <a name="environment-variables"></a>Variáveis de ambiente

As variáveis de ambiente podem ser usadas para fornecer algumas informações de configuração em tempo de execução. Os botões de configuração especificados como variáveis de ambiente geralmente têm o prefixo **COMPlus_**.

Você pode definir variáveis de ambiente a partir do Painel de Controle <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> do Windows, na linha de comando ou programáticamente chamando o método em sistemas baseados no Windows e Unix.

Os exemplos a seguir mostram como definir uma variável de ambiente na linha de comando:

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
