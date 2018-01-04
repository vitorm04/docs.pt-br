---
title: Atributo mc:ProcessContent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fe43e2450c35d976db7a188f854f7864f298afc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mcprocesscontent-attribute"></a>Atributo mc:ProcessContent
Especifica qual [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementos ainda devem ter conteúdo processado pelos elementos pai relevantes, mesmo se o elemento pai imediato pode ser ignorado por um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador devido à especificação de [mc: atributo ignorável](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) . O atributo `mc:ProcessContent` dá suporte à compatibilidade de marcação para o mapeamento de namespace personalizado e para controle de versão de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
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
|*[conteúdo]*|*ThisElementCanBeIgnored* está marcado como ignorável. Se o processador ignora esse elemento, *[conteúdo]* é processado pelo *objeto*.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorará o conteúdo dentro de um elemento ignorado. Você pode especificar um elemento específico por `mc:ProcessContent`e um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador continuará a processar o conteúdo dentro do elemento ignorado. Isso normalmente seria usado se o conteúdo é aninhado em várias marcas, pelo menos um dos quais é ignorado e pelo menos um dos quais não é ignorável.  
  
 Vários prefixos podem ser especificados no atributo, usando um separador de espaço, por exemplo: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 O namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] define outros elementos e atributos que não estão documentados dentro desta área do [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. Para obter mais informações, consulte [Especificação de compatibilidade de marcação XML](http://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Consulte também  
 [Atributo mc:Ignorable](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
