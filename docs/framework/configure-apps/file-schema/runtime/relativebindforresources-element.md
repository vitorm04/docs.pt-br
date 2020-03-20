---
title: Elemento <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153900"
---
# <a name="relativebindforresources-element"></a>\<elemento> relativeBindForResources
Otimiza o teste para assemblies satélites.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bindForResources>**  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o tempo de execução do idioma comum otimiza a sonda para conjuntos de satélites.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|O tempo de execução não otimiza a sonda para conjuntos de satélites. Esse é o valor padrão.|  
|`true`|O tempo de execução otimiza a sonda para conjuntos de satélites.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do runtime.|  
  
## <a name="remarks"></a>Comentários  
 Em geral, o Gerenciador de Recursos testa recursos, conforme documentado no tópico [Embalagem e Distribuição de Recursos.](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) Isso significa que, quando o Resource Manager testa uma versão localizada específica de um recurso, ele pode olhar no cache de montagem global, procurar uma pasta <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> específica de cultura na base de código do aplicativo, consultar o Windows Installer para conjuntos de satélites e aumentar o evento. O `<relativeBindForResources>` elemento otimiza a forma como o Resource Manager sonda para conjuntos de satélites. Pode melhorar o desempenho ao sondar recursos nas seguintes condições:  
  
- Quando o conjunto de satélites é implantado no mesmo local que o conjunto de códigos. Em outras palavras, se o conjunto de códigos for instalado no cache de montagem global, os conjuntos de satélites também devem ser instalados lá. Se o conjunto de códigos estiver instalado na base de código do aplicativo, os conjuntos de satélites também devem ser instalados em uma pasta específica de cultura na base de código.  
  
- Quando o Windows Installer não é usado ou é usado apenas raramente para instalação demanda de conjuntos de satélites.  
  
- Quando o código do <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> aplicativo não lida com o evento.  
  
 Definir `enabled` o atributo `true` do elemento para otimizar a `<relativeBindForResources>` sonda do Resource Manager para conjuntos de satélites da seguinte forma:  
  
- Ele usa a localização do conjunto de código sondar para a montagem do satélite.  
  
- Ele não consulta o Windows Installer para conjuntos de satélites.  
  
- Isso não levanta <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> o evento.  
  
## <a name="see-also"></a>Confira também

- [Empacotando e implantando recursos](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
