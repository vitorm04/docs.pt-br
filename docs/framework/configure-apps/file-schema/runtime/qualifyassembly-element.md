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
ms.openlocfilehash: 74e83900c68ab4b3fe01beb3f97657b0140d78ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153913"
---
# <a name="qualifyassembly-element"></a>\<qualificarElemento> Assembly
Especifica o nome completo do assembly que deve ser carregado dinamicamente quando um nome parcial é usado.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<montagem>vinculante**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualificar>de montagem**  
  
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
|`partialName`|Atributo obrigatório.<br /><br /> Especifica o nome parcial do conjunto como aparece no código.|  
|`fullName`|Atributo obrigatório.<br /><br /> Especifica o nome completo da montagem como ela aparece no cache de montagem global.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`assemblyBinding`|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Chamar <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> o método usando nomes de montagem parciais faz com que o tempo de execução do idioma comum procure o conjunto apenas no diretório base do aplicativo. Use ** \<** o elemento qualifyAssembly>no arquivo de configuração do aplicativo para fornecer as informações completas de montagem (nome, versão, token de chave pública e cultura) e faça com que o tempo de execução do idioma comum procure a montagem no cache de montagem global.  
  
 O atributo **fullName** deve incluir os quatro campos de identidade de montagem: nome, versão, token de chave pública e cultura. O **atributo Nome parcial** deve fazer referência parcial a um conjunto. Você deve especificar pelo menos o nome de texto da assembléia (o caso mais comum), mas você também pode incluir versão, token de chave pública ou cultura (ou qualquer combinação dos quatro, mas não todos os quatro). A **parcialNome** deve corresponder ao nome especificado em sua chamada. Por exemplo, você `"math"` não pode especificar como o `Assembly.Load("math, Version=3.3.3.3")` atributo nome **parcial** em seu arquivo de configuração e chamar em seu código.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir, `Assembly.Load("math")` `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`logicamente, transforma a chamada em .  
  
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
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações do runtime](index.md)
- [Como o runtime localiza assemblies](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Referências parciais a assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
