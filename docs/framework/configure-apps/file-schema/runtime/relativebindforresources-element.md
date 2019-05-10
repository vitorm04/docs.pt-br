---
title: Elemento <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15156eaf883fc9ec162e0a85525564d49522b01d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592664"
---
# <a name="relativebindforresources-element"></a>\<relativeBindForResources > elemento
Otimiza o teste para assemblies satélites.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<relativeBindForResources > elemento  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o common language runtime otimiza a investigação de assemblies satélite.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|O tempo de execução não otimiza a investigação de assemblies satélite. Este é o valor padrão.|  
|`true`|O tempo de execução otimiza a investigação de assemblies satélite.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Em geral, o Gerenciador de recursos de investigações para recursos, conforme documentado na [Empacotando e implantando recursos](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tópico. Isso significa que quando investigações do Gerenciador de recursos para uma versão localizada específica de um recurso, ele pode procurar no cache de assembly global, procurar em uma pasta específicas da cultura na consulta do aplicativo de base, de código do Windows Installer para assemblies satélite e acionar o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> eventos. O `<relativeBindForResources>` elemento otimiza a maneira na qual o Gerenciador de recursos investigações para assemblies satélite. Ele pode melhorar o desempenho quando a investigação para recursos nas seguintes condições:  
  
- Quando o assembly satélite é implantado no mesmo local que o assembly de código. Em outras palavras, se o assembly de código estiver instalado no cache de assembly global, os assemblies satélites também devem ser instalados lá. Se o assembly de código estiver instalado na base de código do aplicativo, os assemblies satélites também devem ser instalados em uma pasta específica de cultura na base de código.  
  
- Quando o Windows Installer não é usado ou apenas raramente é usado para instalação sob demanda dos assemblies satélites.  
  
- Quando o código do aplicativo não processa o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> eventos.  
  
 Definindo o `enabled` atributo o `<relativeBindForResources>` elemento a ser `true` otimiza a investigação do Gerenciador de recursos para assemblies satélite da seguinte maneira:  
  
- Ele usa o local do assembly de código pai para investigar o assembly satélite.  
  
- Ele não consulta do Windows Installer para assemblies satélite.  
  
- Ele não gere a <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> eventos.  
  
## <a name="see-also"></a>Consulte também

- [Empacotando e implantando recursos](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
