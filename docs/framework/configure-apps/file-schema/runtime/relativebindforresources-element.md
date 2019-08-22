---
title: Elemento <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 859e8a12421ea92aa48c54317e052683eb8e83f8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663491"
---
# <a name="relativebindforresources-element"></a>\<Elemento de > relativeBindForResources
Otimiza o teste para assemblies satélites.  
  
 \<Elemento de > de configuração  
\<Elemento de > de tempo de execução  
\<Elemento de > relativeBindForResources  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o Common Language Runtime otimiza a investigação para assemblies satélite.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|O tempo de execução não otimiza a investigação para assemblies satélite. Este é o valor padrão.|  
|`true`|O tempo de execução otimiza a investigação para assemblies satélite.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Em geral, as investigações do Resource Manager para recursos, conforme documentado no tópico [empacotando e implantando recursos](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) . Isso significa que quando o Gerenciador de recursos investiga uma versão localizada específica de um recurso, ele pode procurar no cache de assembly global, examinar uma pasta específica de cultura na base de código do aplicativo, consultar Windows Installer para assemblies satélites e gerar o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento. O `<relativeBindForResources>` elemento otimiza a maneira como as investigações do Gerenciador de recursos para assemblies satélite. Ele pode melhorar o desempenho ao investigar os recursos sob as seguintes condições:  
  
- Quando o assembly satélite é implantado no mesmo local que o assembly de código. Em outras palavras, se o assembly de código estiver instalado no cache de assembly global, os assemblies satélite também deverão ser instalados lá. Se o assembly de código estiver instalado na base de código do aplicativo, os assemblies satélite também deverão ser instalados em uma pasta específica de cultura na base de código.  
  
- Quando Windows Installer não é usado ou é usado apenas raramente para a instalação sob demanda de assemblies satélite.  
  
- Quando o código do aplicativo não manipula <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> o evento.  
  
 Definir o `enabled` atributo `<relativeBindForResources>` do elemento para `true` otimizar a investigação do Gerenciador de recursos para assemblies satélite da seguinte maneira:  
  
- Ele usa o local do assembly de código pai para investigar o assembly satélite.  
  
- Ele não consulta Windows Installer para assemblies satélite.  
  
- Ele não gera o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento.  
  
## <a name="see-also"></a>Consulte também

- [Empacotando e implantando recursos](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
