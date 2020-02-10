---
title: Atributo mc:ProcessContent
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: bcf55668bdc70902e346c401549a88f6ccb9072e
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095119"
---
# <a name="mcprocesscontent-attribute"></a>Atributo mc:ProcessContent
Especifica quais elementos de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ainda devem ter conteúdo processado por elementos pai relevantes, mesmo que o elemento pai imediato possa ser ignorado por um processador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] devido à especificação do [atributo MC: Ignorable](mc-ignorable-attribute.md). O atributo `mc:ProcessContent` dá suporte à compatibilidade de marcação para o mapeamento de namespace personalizado e para controle de versão de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
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
|*disputa*|*ThisElementCanBeIgnored* está marcado como ignorável. Se o processador ignorar esse elemento, *[content]* será processado por *Object*.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorará o conteúdo dentro de um elemento ignorado. Você pode especificar um elemento específico por `mc:ProcessContent`e um processador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] continuará processando o conteúdo dentro do elemento ignorado. Isso normalmente seria usado se o conteúdo estiver aninhado em várias marcas, pelo menos um dos quais é ignorável e pelo menos um deles não é ignorável.  
  
 Vários prefixos podem ser especificados no atributo, usando um separador de espaço, por exemplo: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 O namespace `http://schemas.openxmlformats.org/markup-compatibility/2006` define outros elementos e atributos que não estão documentados nessa área do SDK. Para obter mais informações, consulte [Especificação de compatibilidade de marcação XML](https://docs.microsoft.com/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Confira também

- [Atributo mc:Ignorable](mc-ignorable-attribute.md)
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
