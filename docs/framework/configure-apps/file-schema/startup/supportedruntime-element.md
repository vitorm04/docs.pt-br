---
title: elemento de configuração <supportedRuntime>-.NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: 5e7fc5f81468ff7c4eba8145ee42a4c7cf8bc0b8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697516"
---
# <a name="supportedruntime-element"></a>\<supportedRuntime > elemento

Especifica qual versão de Common Language Runtime e, opcionalmente, .NET Framework versão à qual o aplicativo dá suporte.  

[\<configuration>](../configuration-element.md)  
&nbsp;&nbsp;[\<startup>](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<supportedRuntime>**  

## <a name="syntax"></a>Sintaxe

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|**version**|Atributo opcional.<br /><br /> Um valor de cadeia de caracteres que especifica a versão do Common Language Runtime (CLR) a qual esse aplicativo oferece suporte. Para obter valores válidos do atributo `version`, consulte a seção ["versão de tempo de execução"](#version) . **Observação:**  Por meio do .NET Framework 3,5, o valor de "*versão de tempo de execução*" assume o formato *principal*. *secundária*. *Compilar*. A partir do .NET Framework 4, somente os números de versão principal e secundária são necessários (ou seja, "v 4.0" em vez de "v 4.0.30319"). A cadeia de caracteres mais curta é recomendada.|
|**sku**|Atributo opcional.<br /><br /> Um valor de cadeia de caracteres que especifica a SKU (unidade de manutenção de estoque) que, por sua vez, especifica para qual versão .NET Framework esse aplicativo dá suporte.<br /><br /> A partir do .NET Framework 4,0, o uso do atributo `sku` é recomendado.  Quando presente, indica a versão do .NET Framework de destino do aplicativo.<br /><br /> Para obter os valores válidos do atributo SKU, consulte a seção ["ID do SKU"](#sku) .|

## <a name="remarks"></a>Comentários

Se o elemento **\<supportedRuntime >** não estiver presente no arquivo de configuração do aplicativo, a versão do tempo de execução usada para criar o aplicativo será usada.

O elemento **\<supportedRuntime >** deve ser usado por todos os aplicativos criados usando a versão 1,1 ou posterior do tempo de execução. Os aplicativos criados para dar suporte apenas à versão 1,0 do tempo de execução devem usar o elemento [\<requiredRuntime >](../startup/requiredruntime-element.md) .

> [!NOTE]
> Se você usar a função [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) para especificar o arquivo de configuração, deverá usar o elemento `<requiredRuntime>` para todas as versões do tempo de execução. O elemento `<supportedRuntime>` é ignorado quando você usa [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Para aplicativos que dão suporte a versões do tempo de execução do .NET Framework 1,1 até 3,5, quando várias versões do tempo de execução têm suporte, o primeiro elemento deve especificar a versão mais preferencial do tempo de execução e o último elemento deve especificar o mínimo versão preferencial. Para aplicativos que dão suporte ao .NET Framework 4,0 ou versões posteriores, o atributo `version` indica a versão do CLR, que é comum para o .NET Framework 4 e versões posteriores, e o atributo `sku` indica a única versão de .NET Framework de destino do aplicativo. 

Se o elemento **\<supportedRuntime >** com o atributo `sku` estiver presente no arquivo de configuração e a versão .NET Framework instalada for menor, a versão especificada com suporte, o aplicativo não será executada e, em vez disso, exibirá um mensagem solicitando a instalação da versão com suporte. Caso contrário, o aplicativo tentará ser executado em qualquer versão instalada, mas poderá se comportar inesperadamente se não for totalmente compatível com essa versão. (Para obter diferenças de compatibilidade entre as versões do .NET Framework, consulte [compatibilidade de aplicativos no .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Portanto, recomendamos que você inclua esse elemento no arquivo de configuração do aplicativo para facilitar o diagnóstico de erros. (O arquivo de configuração gerado automaticamente pelo Visual Studio ao criar um novo projeto já o contém.)
  
> [!NOTE]
> Se seu aplicativo usa caminhos de ativação herdados, como a [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), e você deseja que esses caminhos ativem a versão 4 do CLR em vez de uma versão anterior, ou se seu aplicativo for criado com o .NET Framework 4, mas tiver uma dependência em um assembly de modo misto criado com uma versão anterior do .NET Framework, não é suficiente especificar o .NET Framework 4 na lista de tempos de execução com suporte. Além disso, no [elemento \<startup >](../startup/startup-element.md) no arquivo de configuração, você deve definir o atributo `useLegacyV2RuntimeActivationPolicy` como `true`. No entanto, definir esse atributo como `true` significa que todos os componentes criados com versões anteriores do .NET Framework são executados usando o .NET Framework 4 em vez dos tempos de execução com os quais foram criados.

Recomendamos que você teste aplicativos com todas as versões do .NET Framework na qual eles podem ser executados.

<a name="version"></a> 
## <a name="runtime-version-values"></a>valores de "versão de tempo de execução"
O atributo `runtime` especifica a versão do CLR (Common Language Runtime) necessária para um determinado aplicativo. Observe que todas as versões .NET Framework v4. x especificam o CLR `v4.0`. A tabela a seguir lista os valores válidos para o valor de *versão de tempo de execução* do atributo `version`.

|Versão do .NET Framework|Atributo `version`|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2.0|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3.5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku"></a>valores de "ID do SKU"

O atributo `sku` usa um moniker de estrutura de destino (TFM) para indicar a versão do .NET Framework que o aplicativo se destina e requer para ser executado. A tabela a seguir lista os valores válidos com suporte pelo atributo `sku`, começando com o .NET Framework 4.

|Versão do .NET Framework|Atributo `sku`|
|----------------------------|---------------------|
|4.0|".NETFramework,Version=v4.0"|
|4,0, perfil do cliente|".NETFramework,Version=v4.0,Profile=Client"|
|4,0, atualização de plataforma 1|". NETFramework, versão = v 4.0.1 "|
|4,0, perfil do cliente, atualização 1|".NETFramework,Version=v4.0.1,Profile=Client"|
|4,0, atualização de plataforma 2|". NETFramework, Version = v 4.0.2 "|
|4,0, perfil do cliente, atualização 2|".NETFramework,Version=v4.0.2,Profile=Client"|
|4,0, atualização de plataforma 3|". NETFramework, versão = v 4.0.3 "|
|4,0, perfil do cliente, atualização 3|".NETFramework,Version=v4.0.3,Profile=Client"|
|4.5|".NETFramework,Version=v4.5"|
|4.5.1|".NETFramework,Version=v4.5.1"|
|4.5.2|".NETFramework,Version=v4.5.2"|
|4.6|".NETFramework,Version=v4.6"|
|4.6.1|".NETFramework,Version=v4.6.1"|
|4.6.2|".NETFramework,Version=v4.6.2"|
|4.7|".NETFramework,Version=v4.7"|
|4.7.1|".NETFramework,Version=v4.7.1"|
|4.7.2|". NETFramework, Version = v 4.7.2 "|
|4.8|". NETFramework, versão = v 4.8 "|

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como especificar a versão de tempo de execução com suporte em um arquivo de configuração. O arquivo de configuração indica que o aplicativo tem como alvo o .NET Framework 4,7.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a>arquivo de configuração

Este elemento pode ser usado no arquivo de configuração do aplicativo.

## <a name="see-also"></a>Consulte também

- [Esquema de configurações de inicialização](../startup/index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Execução lado a lado em processo](../../../deployment/in-process-side-by-side-execution.md)
