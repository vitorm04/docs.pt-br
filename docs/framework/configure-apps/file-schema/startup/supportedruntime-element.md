---
title: <supportedRuntime>elemento de configuração - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: e16eb098db4bce115a5f1e043829eb272c952860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153692"
---
# <a name="supportedruntime-element"></a>\<suporteElemento de> runtime

Especifica qual versão de tempo de execução do idioma comum e, opcionalmente, a versão .NET Framework que o aplicativo suporta.  

[\<>de configuração](../configuration-element.md)  
&nbsp;&nbsp;[\<>de startup](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<>de runtime suportado**  

## <a name="syntax"></a>Sintaxe

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|**versão**|Atributo opcional.<br /><br /> Um valor de cadeia de caracteres que especifica a versão do Common Language Runtime (CLR) a qual esse aplicativo oferece suporte. Para obter valores válidos do atributo, `version` consulte a seção ["versão em tempo de execução".](#version) **Nota:**  Através do .NET Framework 3.5, o valor "*runtime*version " assume a forma *principal*. *menor*. *construir*. Começando pelo Quadro .NET 4, apenas os números de versão principal e menor são necessários (ou seja, "v4.0" em vez de "v4.0.30319"). A cadeia de caracteres mais curta é recomendada.|
|**sku**|Atributo opcional.<br /><br /> Um valor de string que especifica a unidade de manutenção de estoque (SKU), que por sua vez especifica qual .NET Framework libera esse aplicativo suporta.<br /><br /> Começando pelo Quadro .NET 4.0, `sku` recomenda-se o uso do atributo.  Quando presente, ele indica a versão do .NET Framework que o aplicativo tem como alvo.<br /><br /> Para obter valores válidos do atributo sku, consulte a seção [de valores "sku id".](#sku)|

## <a name="remarks"></a>Comentários

Se ** \<** o elemento de>runtime suportado não estiver presente no arquivo de configuração do aplicativo, a versão do tempo de execução usado para construir o aplicativo será usada.

O elemento ** \<de>runtime suportado** deve ser usado por todos os aplicativos construídos usando a versão 1.1 ou posterior do tempo de execução. Os aplicativos construídos para suportar apenas a versão 1.0 do tempo de execução devem usar o [ \<elemento requiredRuntime>.](../startup/requiredruntime-element.md)

> [!NOTE]
> Se você usar a função [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) para especificar `<requiredRuntime>` o arquivo de configuração, você deve usar o elemento para todas as versões do tempo de execução. O `<supportedRuntime>` elemento é ignorado quando você usa [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Para aplicativos que suportam versões do tempo de execução do .NET Framework 1.1 a 3.5, quando várias versões do tempo de execução são suportadas, o primeiro elemento deve especificar a versão mais preferida do tempo de execução e o último elemento deve especificar o mínimo versão preferida. Para aplicativos que suportam as versões .NET Framework 4.0 ou posteriores, o atributo `version` indica a `sku` versão CLR, que é comum às versões .NET Framework 4 e posteriores, e o atributo indica a versão única .NET Framework que o aplicativo tem como alvo.

Se o `sku` ** \<** elemento de>de execução com o atributo suportado estiver presente no arquivo de configuração e a versão .NET Framework instalada for menor do que a versão suportada especificada, o aplicativo não será executado e, em vez disso, exibirá uma mensagem pedindo para instalar a versão suportada. Caso contrário, o aplicativo tenta ser executado em qualquer versão instalada, mas pode se comportar inesperadamente se não for totalmente compatível com essa versão. (Para diferenças de compatibilidade entre as versões do .NET Framework, consulte [compatibilidade de aplicativos no .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Portanto, recomendamos que você inclua esse elemento no arquivo de configuração do aplicativo para diagnósticos de erros mais fáceis. (O arquivo de configuração gerado automaticamente pelo Visual Studio ao criar um novo projeto já o contém.)
  
> [!NOTE]
> Se o aplicativo usar caminhos de ativação legados, como a [função CorBindToRuntimeEx,](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)e você quiser que esses caminhos ativem a versão 4 do CLR em vez de uma versão anterior, ou se o aplicativo for construído com o .NET Framework 4, mas tiver uma dependência de um conjunto de modo misto construído com uma versão anterior do .NET Framework, não é suficiente especificar o .NET Framework 4 na lista de tempos de execução suportados. Além disso, no `useLegacyV2RuntimeActivationPolicy` `true` [ \<elemento de inicialização>](../startup/startup-element.md) em seu arquivo de configuração, você deve definir o atributo para . No entanto, `true` definir esse atributo significa que todos os componentes construídos com versões anteriores do .NET Framework são executados usando o .NET Framework 4 em vez dos tempos de execução com os que foram construídos.

Recomendamos que você teste aplicativos com todas as versões do .NET Framework na qual eles podem ser executados.

<a name="version"></a>
## <a name="runtime-version-values"></a>Valores da "versão de tempo de execução"
O `runtime` atributo especifica a versão CLR (Common Language Runtime, tempo de execução do idioma comum) necessária para um determinado aplicativo. Observe que todas as versões do `v4.0` .NET Framework v4.x especificam o CLR. A tabela a seguir lista valores válidos para o valor da *versão em tempo de execução* do atributo. `version`

|Versão do .NET Framework|Atributo `version`|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1,1|"v1.1.4322"|
|2,0|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3,5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku-id-values"></a><a name="sku"></a>Valores "sku id"

O `sku` atributo usa um apelido de estrutura de destino (TFM) para indicar a versão do .NET Framework que o aplicativo tem como alvo e exige para ser executado. A tabela a seguir lista valores `sku` válidos que são suportados pelo atributo, começando pelo Quadro .NET 4.

|Versão do .NET Framework|Atributo `sku`|
|----------------------------|---------------------|
|4,0|". NETFramework,Versão=v4.0"|
|4.0, Perfil do Cliente|". NETFramework,Versão=v4.0,Profile=Client"|
|4.0, atualização da plataforma 1|". NETFramework,Versão=v4.0.1"|
|4.0, Perfil do Cliente, atualização 1|". NETFramework,Versão=v4.0.1,Profile=Client"|
|4.0, atualização da plataforma 2|". NETFramework,Versão=v4.0.2"|
|4.0, Perfil do Cliente, atualização 2|". NETFramework,Versão=v4.0.2,Profile=Client"|
|4.0, atualização da plataforma 3|". NETFramework,Versão=v4.0.3"|
|4.0, Perfil do Cliente, atualização 3|". NETFramework,Versão=v4.0.3,Profile=Client"|
|4.5|". NETFramework,Versão=v4.5"|
|4.5.1|". NETFramework,Versão=v4.5.1"|
|4.5.2|". NETFramework,Versão=v4.5.2"|
|4.6|". NETFramework,Versão=v4.6"|
|4.6.1|". NETFramework,Versão=v4.6.1"|
|4.6.2|". NETFramework,Versão=v4.6.2"|
|4.7|". NETFramework,Versão=v4.7"|
|4.7.1|". NETFramework,Versão=v4.7.1"|
|4.7.2|". NETFramework,Versão=v4.7.2"|
|4.8|". NETFramework,Versão=v4.8"|

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como especificar a versão de tempo de execução suportada em um arquivo de configuração. O arquivo de configuração indica que o aplicativo tem como alvo o .NET Framework 4.7.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a>Arquivo de configuração

Este elemento pode ser usado no arquivo de configuração do aplicativo.

## <a name="see-also"></a>Confira também

- [Esquema de configurações de inicialização](../startup/index.md)
- [Esquema de arquivo de configuração](../index.md)
- [Execução lado a lado em processo](../../../deployment/in-process-side-by-side-execution.md)
