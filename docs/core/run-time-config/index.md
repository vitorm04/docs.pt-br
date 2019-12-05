---
title: Configuração de tempo de execução
description: Saiba como configurar aplicativos .NET Core usando as definições de configuração de tempo de execução.
ms.date: 11/13/2019
ms.openlocfilehash: 2665026347e94d26026821beb2bfcf8441f755f6
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801921"
---
# <a name="net-core-run-time-configuration-settings"></a>Definições de configuração de tempo de execução do .NET Core

O .NET Core dá suporte ao uso de arquivos de configuração e variáveis de ambiente para configurar o comportamento de aplicativos .NET Core em tempo de execução. A configuração de tempo de execução é uma opção atraente se:

- Você não possui ou controla o código-fonte de um aplicativo e, portanto, não é possível configurá-lo programaticamente.

- Várias instâncias do seu aplicativo são executadas ao mesmo tempo em um único sistema e você deseja configurar cada uma para obter um desempenho ideal.

> [!NOTE]
> Esta documentação é um trabalho em andamento. Se você observar que as informações apresentadas aqui estão incompletas ou imprecisas, [abra um problema](https://github.com/dotnet/docs/issues) para nos informar sobre ela ou [envie uma solicitação de pull](https://github.com/dotnet/docs/pulls) para resolver o problema. Para obter informações sobre como enviar solicitações pull para o repositório dotnet/docs, consulte o [Guia do colaborador](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).

O .NET Core fornece os seguintes mecanismos para configurar aplicativos em tempo de execução:

- O [arquivo runtimeconfig. JSON](#runtimeconfigjson)

- [Variáveis de ambiente](#environment-variables)

Os artigos nesta seção da documentação incluem são organizados por categoria, por exemplo, depuração e coleta de lixo. Quando aplicável, as opções de configuração são mostradas para *runtimeconfig. JSON* (somente no .NET Core), *app. config* (somente .NET Framework) e variáveis de ambiente.

## <a name="runtimeconfigjson"></a>runtimeconfig. JSON

Especifique as opções de configuração de tempo de execução na seção **configproperties** do arquivo *runtimeconfig. JSON* do aplicativo. Esta seção tem o formato:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

Este é um arquivo de exemplo:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

O arquivo *runtimeconfig. JSON* é criado automaticamente no diretório de compilação pelo comando [dotnet Build](../tools/dotnet-build.md) . Ele também é criado quando você seleciona a opção de menu **Build** no Visual Studio. Em seguida, você pode editar o arquivo depois de ele ser criado.

Alguns valores de configuração também podem ser definidos programaticamente chamando o método <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.

## <a name="environment-variables"></a>Variáveis de ambiente

As variáveis de ambiente podem ser usadas para fornecer algumas informações de configuração de tempo de execução. Os botões de configuração especificados como variáveis de ambiente geralmente têm o prefixo **COMPlus_** .

Você pode definir variáveis de ambiente no painel de controle do Windows, na linha de comando ou programaticamente chamando o método <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> em sistemas baseados no Windows e no UNIX.

Os exemplos a seguir mostram como definir uma variável de ambiente na linha de comando:

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
