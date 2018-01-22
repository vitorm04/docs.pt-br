---
title: '&lt;requiredRuntime&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2e864eec2ddf51d5cc88110654f6c23f146938d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltrequiredruntimegt-element"></a>&lt;requiredRuntime&gt; elemento
Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime. Esse elemento foi preterido e não deve mais ser usado. O [ `supportedRuntime` ](supportedruntime-element.md) elemento deve ser usado em vez disso.
  
 \<configuration>  
\<startup>  
\<requiredRuntime>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`version`|Atributo opcional.<br /><br /> Um valor de cadeia de caracteres que especifica a versão do .NET Framework que oferece suporte a esse aplicativo. O valor de cadeia de caracteres deve corresponder ao nome de diretório localizado na raiz de instalação do .NET Framework. O conteúdo do valor de cadeia de caracteres não é analisado.|  
|`safemode`|Atributo opcional.<br /><br /> Especifica se o código de inicialização do tempo de execução procura o registro para determinar a versão de tempo de execução.|  
  
## <a name="safemode-attribute"></a>Atributo de modo de segurança  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|O código de inicialização do tempo de execução é no registro. Este é o valor padrão.|  
|`true`|O código de inicialização do tempo de execução não procura no registro.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`startup`|Contém o `<requiredRuntime>` elemento.|  
  
## <a name="remarks"></a>Comentários  
 Os aplicativos criados para oferecer suporte a apenas versão 1.0 do tempo de execução devem usar o `<requiredRuntime>` elemento. Os aplicativos criados com a versão 1.1 ou posterior do tempo de execução devem usar o `<supportedRuntime>` elemento.  
  
> [!NOTE]
>  Se você usar o [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) de função para especificar o arquivo de configuração, você deve usar o `<requiredRuntime>` elemento para todas as versões do tempo de execução. O `<supportedRuntime>` elemento será ignorado quando você usar [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
 O `version` cadeia de caracteres do atributo deve corresponder ao nome de pasta de instalação para a versão especificada do .NET Framework. Essa cadeia de caracteres não é interpretada. Se o código de inicialização do tempo de execução não encontrar uma pasta correspondente, o tempo de execução não será carregado; o código de inicialização mostra uma mensagem de erro e sai.  
  
> [!NOTE]
>  O código de inicialização para um aplicativo que é hospedado no Microsoft Internet Explorer ignora o `<requiredRuntime>` elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações de inicialização](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2) (PaveOver> Especificando a versão do tempo de execução a ser usada)
