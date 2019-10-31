---
title: Elemento <qualifyAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 17cfe9fc39d65f146beef5d02c701f5e3e2fbbe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115778"
---
# <a name="qualifyassembly-element"></a>\<elemento de > qualifyAssembly
Especifica o nome completo do assembly que deve ser carregado dinamicamente quando um nome parcial é usado.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp; &nbsp; &nbsp; &nbsp;[ **\<assemblyBinding**](assemblybinding-element-for-runtime.md) > \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<qualifyAssembly >**  
  
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
 Chamar o método <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> usando nomes de assembly parciais faz com que a Common Language Runtime procure o assembly somente no diretório base do aplicativo. Use o elemento **\<qualifyAssembly >** no arquivo de configuração do aplicativo para fornecer as informações completas do assembly (nome, versão, token de chave pública e cultura) e fazer com que a Common Language Runtime procure o assembly no global cache de assembly.  
  
 O atributo **FullName** deve incluir os quatro campos da identidade do assembly: nome, versão, token de chave pública e cultura. O atributo **partialName** deve fazer referência parcial a um assembly. Você deve especificar pelo menos o nome de texto do assembly (o caso mais comum), mas também pode incluir a versão, o token de chave pública ou a cultura (ou qualquer combinação dos quatro, mas não todos os quatro). O **partialName** deve corresponder ao nome especificado em sua chamada. Por exemplo, você não pode especificar `"math"` como o atributo **partialName** no arquivo de configuração e chamar `Assembly.Load("math, Version=3.3.3.3")` em seu código.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir transforma logicamente a chamada `Assembly.Load("math")` em `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
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

- [Esquema de configurações do tempo de execução](index.md)
- [Como o tempo de execução localiza assemblies](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Referências parciais de assembly](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
