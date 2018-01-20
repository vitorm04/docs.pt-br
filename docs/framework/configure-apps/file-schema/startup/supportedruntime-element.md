---
title: '&lt;supportedRuntime&gt; elemento'
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4b0967790f2bbf8fa9a889c56fa9c5168f7523bd
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2018
---
# <a name="ltsupportedruntimegt-element"></a>&lt;supportedRuntime&gt; elemento

Especifica a quais versões do Common Language Runtime o aplicativo oferece suporte. Este elemento deve ser usado por todos os aplicativos criados com a versão 1.1 ou posterior do .NET Framework.  
  
[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
&nbsp;&nbsp;[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**  
  
## <a name="syntax"></a>Sintaxe
  
```xml  
<supportedRuntime version="runtime version" sku="sku id"/>  
```  
  
## <a name="attributes"></a>Atributos
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**version**|Atributo opcional.<br /><br /> Um valor de cadeia de caracteres que especifica a versão do Common Language Runtime (CLR) a qual esse aplicativo oferece suporte. Para obter valores válidos do `version` de atributo, consulte o [valores de "versão de tempo de execução"](#version) seção. **Observação:** por meio do .NET Framework 3.5, o "*versão de tempo de execução*" valor assume a forma *principais*. *pequenas*. *criar*. A partir do [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], somente os números das versões principal e secundária são necessários (isto é, "v4.0" em vez de "v4.0.30319"). A cadeia de caracteres mais curta é recomendada.|  
|**sku**|Atributo opcional.<br /><br /> Um valor de cadeia de caracteres que especifica a unidade de manutenção de estoque (SKU), que por sua vez Especifica qual versão do .NET Framework oferece suporte a esse aplicativo.<br /><br /> Começando com o .NET Framework 4.0, o uso do `sku` atributo é recomendado.  Quando presente, indica a versão do .NET Framework que o aplicativo é destinado.<br /><br /> Para obter valores válidos do atributo sku, consulte o [valores de "id do sku"](#sku) seção.|  
  
## <a name="remarks"></a>Comentários

Se o  **\<supportedRuntime >** elemento não está presente no arquivo de configuração do aplicativo, a versão do tempo de execução usada para criar o aplicativo é usada.  

O  **\<supportedRuntime >** elemento deve ser usado por todos os aplicativos criados com a versão 1.1 ou posterior do tempo de execução. Os aplicativos criados para oferecer suporte a apenas versão 1.0 do tempo de execução devem usar o [ \<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) elemento.  
  
> [!NOTE]
>  Se você usar o [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) de função para especificar o arquivo de configuração, você deve usar o `<requiredRuntime>` elemento para todas as versões do tempo de execução. O `<supportedRuntime>` elemento será ignorado quando você usar [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Para aplicativos que dão suporte a versões do tempo de execução do .NET Framework 1.1 por meio de 3.5, quando há suporte para várias versões do tempo de execução, o primeiro elemento deve especificar a versão preferida do tempo de execução e o último elemento deve especificar o menor versão preferencial. Para aplicativos que dão suporte a .NET Framework 4.0 ou versões posteriores, o `version` atributo indica a versão do CLR, que é comum para o .NET Framework 4 e versões posteriores, e o `sku` única versão do .NET Framework do atributo indica que o aplicativo destinos.  
  
> [!NOTE]
>  Se seu aplicativo usa caminhos de ativação herdadas, como o [função CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), e você deseja que esses caminhos para ativar a versão 4 do CLR em vez de uma versão anterior, ou se seu aplicativo é criado com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], mas tem uma dependência em um assembly de modo misto foi compilado com uma versão anterior do .NET Framework, não é suficiente especificar o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] na lista de tempos de execução com suporte. Além disso, no [ \<inicialização > elemento](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) no arquivo de configuração, você deve definir o `useLegacyV2RuntimeActivationPolicy` atributo `true`. No entanto, definir esse atributo como `true` significa que todos os componentes criados com versões anteriores do .NET Framework serão executados usando [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] em vez dos tempos de execução com os quais foram criados.  
  
Recomendamos que você teste aplicativos com todas as versões do .NET Framework na qual eles podem ser executados.  
  
<a name="version"></a>   
## <a name="runtime-version-values"></a>valores de "versão de tempo de execução"  
O `runtime` atributo especifica a versão do Common Language Runtime (CLR) que é necessária para um determinado aplicativo. Observe que todas as versões do .NET Framework versão 4. x especificar o `v4.0` CLR. A tabela a seguir lista os valores válidos para o *versão de tempo de execução* valor o `version` atributo.  

|Versão do .NET Framework|Atributo `version`|  
|----------------------------|-------------------------|  
|1.0|"v1.0.3705"|  
|1.1|"v1.1.4322"|  
|2.0|"v2.0.50727"|  
|3.0|"v2.0.50727"|  
|3.5|"v2.0.50727"|  
|4.0-4.7.1|"v4.0"|  

<a name="sku"></a>   
## <a name="sku-id-values"></a>valores de "id do sku"

O `sku` atributo usa um moniker do framework de destino (TFM) para indicar a versão do .NET Framework que o aplicativo tem como alvo e precisa ser executado. A tabela a seguir lista os valores válidos são suportados pelo `sku` atributo, começando com o .NET Framework 4.
  
|Versão do .NET Framework|Atributo `sku`|  
|----------------------------|---------------------|  
|4.0|".NETFramework,Version=v4.0"|  
|4.0, o perfil de cliente|".NETFramework,Version=v4.0,Profile=Client"|  
|atualização da plataforma 4.0, 1|.NETFramework,Version=v4.0.1|  
|4.0, o perfil de cliente da atualização 1|.NETFramework,Version=v4.0.1,Profile=Client|  
|atualização da plataforma 4.0, 2|.NETFramework,Version=v4.0.2|  
|4.0, perfil do cliente, atualização 2|.NETFramework,Version=v4.0.2,Profile=Client|  
|atualização da plataforma 4.0, 3|.NETFramework,Version=v4.0.3|  
|4.0, perfil do cliente, a atualização 3|.NETFramework,Version=v4.0.3,Profile=Client|  
|4.5|".NETFramework,Version=v4.5"|  
|4.5.1|".NETFramework,Version=v4.5.1"|  
|4.5.2|".NETFramework,Version=v4.5.2"|  
|4.6|".NETFramework,Version=v4.6"|  
|4.6.1|".NETFramework,Version=v4.6.1"|  
|4.6.2|".NETFramework,Version=v4.6.2"|  
|4.7|".NETFramework,Version=v4.7"|
|4.7.1|".NETFramework,Version=v4.7.1"|

## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar a versão de tempo de execução com suporte em um arquivo de configuração. O arquivo de configuração indica que o aplicativo tem como alvo o .NET Framework 4.7.  
  
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

 [Esquema de configurações de inicialização](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Execução lado a lado em processo](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)  
