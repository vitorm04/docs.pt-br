---
title: Atributo mc:ProcessContent
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: 865b1a3ccc30ff5efab4b08956bf7ba2bba4769c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110580"
---
# <a name="mcprocesscontent-attribute"></a>Atributo mc:ProcessContent
Especifica qual [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementos ainda devem ter conteúdo processado pelos elementos pai relevantes, mesmo se o elemento pai imediato pode ser ignorado por um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador devido à especificação [mc: Ignorable Attribute](mc-ignorable-attribute.md) . O atributo `mc:ProcessContent` dá suporte à compatibilidade de marcação para o mapeamento de namespace personalizado e para controle de versão de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*ignorablePrefix*|Qualquer cadeia de caracteres de prefixo é válida, conforme a especificação de XML 1.0.|  
|*ignorableUri*|Qualquer URI válido para designar um namespace, conforme a especificação XML 1.0.|  
|*ThisElementCanBeIgnored*|Um elemento que poderá ser ignorado por implementações do processador [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], se o tipo subjacente não puder ser resolvido.|  
|*[content]*|*ThisElementCanBeIgnored* está marcado como ignorável. Se o processador ignora esse elemento, *[conteúdo]* é processado pelo *objeto*.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorará o conteúdo dentro de um elemento ignorado. Você pode especificar um elemento específico por `mc:ProcessContent`e um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador continuará a processar o conteúdo dentro do elemento ignorado. Isso normalmente seria usado se o conteúdo estiver aninhado em várias marcas, pelo menos um dos quais é ignorado e pelo menos um dos quais não pode ser ignorado.  
  
 Vários prefixos podem ser especificados no atributo, usando um separador de espaço, por exemplo: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 O namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] define outros elementos e atributos que não estão documentados dentro desta área do [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. Para obter mais informações, consulte [Especificação de compatibilidade de marcação XML](https://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Consulte também

- [Atributo mc:Ignorable](mc-ignorable-attribute.md)
- [Visão geral de XAML (WPF)](xaml-overview-wpf.md)
