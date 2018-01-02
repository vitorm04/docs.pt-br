---
title: '&lt;disableCachingBindingFailures&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd86bc2f58bc216f741c32a51925d3f4f8ef47df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a>&lt;disableCachingBindingFailures&gt; elemento
Especifica se é necessário desabilitar o cache de associação de falhas que ocorrem porque o assembly não foi encontrado por sondagem.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<disableCachingBindingFailures >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Habilitado|Atributo obrigatório.<br /><br /> Especifica se é necessário desabilitar o cache de associação de falhas que ocorrem porque o assembly não foi encontrado por sondagem.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|0|Não desabilite o cache de associação de falhas que ocorrem porque o assembly não foi encontrado por sondagem. Esse é o comportamento de associação padrão iniciando com o .NET Framework versão 2.0.|  
|1|Desabilite o cache de associação de falhas que ocorrem porque o assembly não foi encontrado por sondagem. Essa configuração será revertido para o comportamento de associação do .NET Framework versão 1.1.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Iniciando com o .NET Framework versão 2.0, o comportamento padrão de carregamento de assemblies é armazenar em cache todas as falhas de carregamento e associação. Ou seja, se houver falha na tentativa de carregar um assembly, solicitações subsequentes para carregar o mesmo assembly falham imediatamente, sem qualquer tentativa de localizar o assembly. Este elemento desativa o comportamento padrão para falhas que ocorrem porque o assembly não pôde ser encontrado no caminho de investigação de associação. Essas falhas lançam <xref:System.IO.FileNotFoundException>.  
  
 Associação de algumas falhas de carregamento não são afetados por este elemento e sempre são armazenados em cache. Essas falhas ocorrem porque o assembly foi encontrado, mas não pôde ser carregado. Eles geram <xref:System.BadImageFormatException> ou <xref:System.IO.FileLoadException>. A lista a seguir inclui alguns exemplos de tais falhas.  
  
-   Se você tentar carregar um arquivo não é um assembly válido, as tentativas subsequentes para carregar o assembly falhará mesmo que o arquivo inválido é substituído com o assembly correto.  
  
-   Se você tentar carregar um assembly que está bloqueado pelo sistema de arquivos, as tentativas subsequentes para carregar o assembly falhará mesmo depois que o assembly é liberado pelo sistema de arquivos.  
  
-   Se uma ou mais versões do assembly que você está tentando carregar está no caminho de investigação, mas a versão específica que você está solicitando não está entre eles, tentativas subsequentes para carregar dessa versão falhará mesmo se a versão correta é movida para o caminho de investigação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como desabilitar o cache de falhas de associação de assembly que ocorrem porque o assembly não foi encontrado por sondagem.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Como o tempo de execução localiza assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
