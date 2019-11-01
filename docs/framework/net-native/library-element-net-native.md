---
title: <Library> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128362"
---
# <a name="library-element-net-native"></a>Elemento de > de biblioteca de \<(.NET Native)
Define o assembly que contém tipos e membros de tipo cujos metadados estão disponíveis para reflexão em tempo de execução.  
  
 Elemento \<Directives>  
Elemento \<Library>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Atributo obrigatório. Especifica o nome de um assembly. Elementos filhos deste elemento `<Library>` define a política de reflexão do tempo de execução para tipos e membros de tipo encontrados neste assembly.|  
  
## <a name="name-attribute"></a>Atributo de nome  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*assembly_name*|O nome simples do assembly, sem a extensão de arquivo. Este atributo corresponde à propriedade <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> . Por exemplo, o nome de um assembly denominado Extensions.dll é "Extensions". Consulte a seção Comentários para ver uma forma especial de *assembly_name* que dá suporte à inclusão condicional de metadados do assembly.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|Aplica a política a todos os tipos em um assembly específico.|  
|[\<Namespace>](namespace-element-net-native.md)|Aplica a política a todos os tipos em um namespace específico.|  
|[\<Type>](type-element-net-native.md)|Aplica a política a um tipo específico, como uma classe ou estrutura.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Aplica a política a um tipo genérico construído. Por exemplo, um elemento [\<TypeInstantiation>](typeinstantiation-element-net-native.md) pode ser usado para definir a política para um tipo `List<String>`.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|O elemento raiz de um arquivo de diretivas de runtime.|  
  
## <a name="remarks"></a>Comentários  
 O elemento [\<Directives>](directives-element-net-native.md) pode conter zero, um ou mais elementos `<Library>`.  
  
 O elemento `<Library>` serve como um contêiner para definir os elementos do programa cujos metadados são necessária no tempo de execução. Este elemento não expressa política. No tempo de compilação, as ferramentas do compilador pesquisam somente a biblioteca designada pelo elemento `<Library>` para os elementos do programa identificados por seus elementos filho. Em contraste, as ferramentas do compilador pesquisam todas as bibliotecas, incluindo as bibliotecas principais do .NET Framework, por elementos de programa identificados por elementos filhos do elemento [\<Application>](application-element-net-native.md) elemento.  
  
 As diretivas `<Library>` podem ser utilizadas condicionalmente. Se o nome do elemento de `<Library>` iniciar e terminar com um asterisco (\*), a diretiva de `<Library>` terá efeito somente se o assembly especificado entre os asteriscos for referenciado pelo aplicativo. Por exemplo, a diretiva de tempo de execução a seguir se aplica somente se o assembly Utilities. dll for referenciado pelo aplicativo.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Consulte também

- [Elemento de > de aplicativo \<](application-element-net-native.md)
- [Elemento de > de diretivas de \<](directives-element-net-native.md)
- [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementos da diretiva de tempo de execução](runtime-directive-elements.md)
