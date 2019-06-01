---
title: <supportedRuntime> elemento de configuração - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: c6bf4c6b262bc9066277a683d5eda67ada6f4d08
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456219"
---
# <a name="supportedruntime-element"></a>\<supportedRuntime > elemento

Especifica qual versão do common language runtime e, opcionalmente, o aplicativo de versão do .NET Framework dá suporte.  

[\<configuration>](../configuration-element.md)  
&nbsp;&nbsp;[\<startup>](../startup/startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<supportedRuntime>**  

## <a name="syntax"></a>Sintaxe

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|**version**|Atributo opcional.<br /><br /> Um valor de cadeia de caracteres que especifica a versão do Common Language Runtime (CLR) a qual esse aplicativo oferece suporte. Para obter valores válidos do `version` atributo, consulte a [valores de "versão de tempo de execução"](#version) seção. **Observação:**  Por meio do .NET Framework 3.5, o "*versão de tempo de execução*" valor assume a forma *principais*. *pequenas*. *criar*. A partir do [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], somente os números das versões principal e secundária são necessários (isto é, "v4.0" em vez de "v4.0.30319"). A cadeia de caracteres mais curta é recomendada.|
|**sku**|Atributo opcional.<br /><br /> Um valor de cadeia de caracteres que especifica a unidade de manutenção de estoque (SKU), que por sua vez Especifica qual versão do .NET Framework dá suporte a esse aplicativo.<br /><br /> Começando com o .NET Framework 4.0, o uso do `sku` atributo é recomendado.  Quando presente, indica a versão do .NET Framework que o destino do aplicativo.<br /><br /> Para obter valores válidos do atributo sku, consulte o [valores de "id de sku"](#sku) seção.|

## <a name="remarks"></a>Comentários

Se o  **\<supportedRuntime >** elemento não estiver presente no arquivo de configuração do aplicativo, a versão do tempo de execução usado para compilar o aplicativo é usada.

O  **\<supportedRuntime >** elemento deve ser usado por todos os aplicativos criados usando a versão 1.1 ou posterior do tempo de execução. Os aplicativos criados para oferecer suporte somente à versão 1.0 do tempo de execução devem usar o [ \<requiredRuntime >](../startup/requiredruntime-element.md) elemento.

> [!NOTE]
> Se você usar o [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) para especificar o arquivo de configuração de função, você deve usar o `<requiredRuntime>` elemento para todas as versões do tempo de execução. O `<supportedRuntime>` elemento é ignorado quando você usa [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Para aplicativos que dão suporte a versões do tempo de execução do .NET Framework 1.1, por meio do 3.5, quando há suporte para várias versões do tempo de execução, o primeiro elemento deve especificar a versão preferencial do tempo de execução e o último elemento deve especificar o menor versão de preferência. Para aplicativos que dão suporte a .NET Framework 4.0 ou versões posteriores, o `version` atributo indica a versão do CLR, que é comum para o .NET Framework 4 e versões posteriores, e o `sku` atributo indica a única versão do .NET Framework que o destino do aplicativo. 

Se o  **\<supportedRuntime >** elemento com o `sku` atributo estiver presente no arquivo de configuração e a versão instalada do .NET Framework for inferior a versão com suporte especificada, o aplicativo Falha na execução e exibirá uma mensagem solicitando a instalação da versão com suporte. Caso contrário, o aplicativo tenta executar em qualquer versão instalada, mas ele talvez tenha um comportamento inesperado se ele não é totalmente compatível com essa versão. (As diferenças de compatibilidade entre versões do .NET Framework, consulte [compatibilidade de aplicativos no .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Portanto, é recomendável que você inclua esse elemento no arquivo de configuração de aplicativo para o diagnóstico de erro mais fácil. (O arquivo de configuração gerado automaticamente pelo Visual Studio ao criar um novo projeto já contém-lo.)
  
> [!NOTE]
> Se seu aplicativo usa caminhos de ativação herdados, como o [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), e você deseja esses caminhos para ativar a versão 4 do CLR em vez de uma versão anterior, ou se seu aplicativo é criado com o .NET Framework 4, mas tem uma dependência em um assembly de modo misto criado com uma versão anterior do .NET Framework, não é suficiente especificar o .NET Framework 4 na lista de tempos de execução com suporte. Além disso, nos [ \<inicialização > elemento](../startup/startup-element.md) em seu arquivo de configuração, você deve definir a `useLegacyV2RuntimeActivationPolicy` atributo `true`. No entanto, definir esse atributo como `true` significa que todos os componentes criados com versões anteriores do .NET Framework são executados usando o .NET Framework 4, em vez dos tempos de execução que eles foram criados.

Recomendamos que você teste aplicativos com todas as versões do .NET Framework na qual eles podem ser executados.

<a name="version"></a> 
## <a name="runtime-version-values"></a>valores de "versão de tempo de execução"
O `runtime` atributo especifica a versão de tempo de execução de linguagem comum (CLR) que é necessária para um determinado aplicativo. Observe que todas as versões do .NET Framework versão 4. x especificam o `v4.0` CLR. A tabela a seguir lista os valores válidos para o *versão de tempo de execução* valor o `version` atributo.

|Versão do .NET Framework|`version` Atributo|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2.0|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3.5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku"></a> valores de "id de sku"

O `sku` atributo usa um moniker de estrutura de destino (TFM) para indicar a versão do .NET Framework que o aplicativo tem como alvo e precisa para ser executado. A tabela a seguir lista os valores válidos são compatíveis com o `sku` atributo, começando com o .NET Framework 4.

|Versão do .NET Framework|`sku` Atributo|
|----------------------------|---------------------|
|4.0|".NETFramework,Version=v4.0"|
|4.0, o perfil de cliente|".NETFramework,Version=v4.0,Profile=Client"|
|atualização 1 da plataforma 4.0,|".NETFramework,Version=v4.0.1"|
|4.0, o perfil de cliente, a atualização 1|".NETFramework,Version=v4.0.1,Profile=Client"|
|atualização da plataforma do 4.0, 2|".NETFramework,Version=v4.0.2"|
|4.0, o perfil de cliente, atualização 2|".NETFramework,Version=v4.0.2,Profile=Client"|
|atualização da plataforma do 4.0, 3|".NETFramework,Version=v4.0.3"|
|4.0, o perfil de cliente, a atualização 3|".NETFramework,Version=v4.0.3,Profile=Client"|
|4.5|".NETFramework,Version=v4.5"|
|4.5.1|".NETFramework,Version=v4.5.1"|
|4.5.2|".NETFramework,Version=v4.5.2"|
|4.6|".NETFramework,Version=v4.6"|
|4.6.1|".NETFramework,Version=v4.6.1"|
|4.6.2|".NETFramework,Version=v4.6.2"|
|4.7|".NETFramework,Version=v4.7"|
|4.7.1|".NETFramework,Version=v4.7.1"|
|4.7.2|".NETFramework,Version=v4.7.2"|
|4.8|". NETFramework, versão = v 4.8 "|

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

- [Esquema de configurações de inicialização](../startup/index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Execução lado a lado em processo](../../../deployment/in-process-side-by-side-execution.md)
