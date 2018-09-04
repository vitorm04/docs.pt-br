---
title: '&lt;qualifyAssembly&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59e3f54f4d3ce0c191193ff63a3c2bce5b93a1bd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538025"
---
# <a name="ltqualifyassemblygt-element"></a>&lt;qualifyAssembly&gt; elemento
Especifica o nome completo do assembly que deve ser carregado dinamicamente quando um nome parcial é usado.  
  
 \<configuration>  
\<runtime>  
\<assemblyBinding>  
\<qualifyAssembly>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`partialName`|Atributo obrigatório.<br /><br /> Especifica o nome parcial do assembly como ele aparece no código.|  
|`fullName`|Atributo obrigatório.<br /><br /> Especifica o nome completo do assembly como ele aparece no cache de assembly global.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`assemblyBinding`|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Chamar o <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> método usando nomes de assembly parciais faz com que o common language runtime procurar o assembly apenas no diretório base do aplicativo. Use o  **\<qualifyAssembly >** elemento no arquivo de configuração de aplicativo para fornecer as informações de assembly completa (nome, versão, token de chave pública e cultura) e fazer com que o common language runtime pesquisar para o assembly no cache de assembly global.  
  
 O **fullName** atributo deve incluir os quatro campos de identidade do assembly: nome, versão, token de chave pública e cultura. O **partialName** atributo parcialmente deve fazer referência a um assembly. Você deve especificar pelo menos o nome do assembly texto (o caso mais comum), mas você também pode incluir a versão, token de chave pública ou cultura (ou qualquer combinação de quatro, mas não todos os quatro). O **partialName** deve corresponder ao nome especificado em sua chamada. Por exemplo, você não pode especificar `"math"` como o **partialName** atributo em seu arquivo de configuração e chame `Assembly.Load("math, Version=3.3.3.3")` em seu código.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ativa a chamada a logicamente `Assembly.Load("math")` em `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Como o tempo de execução localiza assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [NIB: Referências de Assembly parcial](https://msdn.microsoft.com/library/ec90f07a-398c-4306-9401-0fc5ff9cb59f)
