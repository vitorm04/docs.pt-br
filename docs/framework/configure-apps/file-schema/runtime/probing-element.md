---
title: '&lt;investigação&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 711903656d8bcce3a2d213af68160707a55a48e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699994"
---
# <a name="ltprobinggt-element"></a>&lt;investigação&gt; elemento
Especifica os subdiretórios do aplicativo base para o common language runtime quando o carregamento de assemblies de pesquisa.  
  
 \<configuration>  
\<runtime>  
\<assemblyBinding>  
\<investigação >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`privatePath`|Atributo obrigatório.<br /><br /> Especifica os subdiretórios do diretório de base do aplicativo que podem conter assemblies. Delimite cada subdiretório com um ponto e vírgula.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`assemblyBinding`|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar o tempo de execução deve procurar assemblies de base e subdiretórios do aplicativo.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Especificando o local de um assembly](../../../../../docs/framework/configure-apps/specify-assembly-location.md)
- [Como o tempo de execução localiza assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
