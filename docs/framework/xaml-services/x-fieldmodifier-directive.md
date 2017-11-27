---
title: Diretiva x:FieldModifier
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 77745744c0da1e4b4425af6d8e4319faaf524908
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xfieldmodifier-directive"></a>Diretiva x:FieldModifier
Modifica o comportamento de compilação XAML, de modo que os campos para referências de objeto nomeado são definidos com <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> acessar em vez do <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> comportamento padrão.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*Público*|A cadeia de caracteres exata que você transmitir para especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varia, dependendo da linguagem de programação por trás do código que é usada. Consulte Observações.|  
  
## <a name="dependencies"></a>Dependências  
 Se uma produção XAML usa `x:FieldModifier` em qualquer lugar, o elemento raiz de produção que XAML deve declarar um [diretiva X:Class](../../../docs/framework/xaml-services/x-class-directive.md).  
  
## <a name="remarks"></a>Comentários  
 `x:FieldModifier`não é relevante para declarar o nível de acesso geral de uma classe ou seus membros. Ele é relevante apenas para o comportamento de processamento de XAML quando um objeto específico do XAML que faz parte de uma produção XAML é processado e se torna um objeto que é potencialmente acessível no gráfico de objeto de um aplicativo. Por padrão, a referência de campo para tal objeto é mantida privada, que impede que os consumidores de controle de modificar o gráfico de objeto diretamente. Em vez disso, os consumidores de controle são esperados para modificar o gráfico de objeto usando padrões que são habilitados por modelos de programação, como Obtendo a raiz de layout, o filho coleções de elementos, as propriedades públicas dedicadas, e assim por diante.  
  
 O valor para o `x:FieldModifier` atributo varia por linguagem de programação e sua finalidade pode variar em estruturas específicas. A cadeia de caracteres a ser usado depende de como cada linguagem implementa seu <xref:System.CodeDom.Compiler.CodeDomProvider> e conversores de tipo que ele retorna para definir os significados de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, e se o idioma diferencia maiusculas de minúsculas.  
  
-   Para [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], a cadeia de caracteres para passar para designar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é `public`.  
  
-   Para [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], a cadeia de caracteres para passar para designar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é `Public`.  
  
-   Para [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], nenhum destino para XAML existe; portanto, a cadeia de caracteres para passar é indefinida.  
  
 Você também pode especificar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` na [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Friend` na [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) mas especificando <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é incomum porque `NotPublic` como o comportamento já é o padrão.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>é o comportamento padrão porque é incomum que código fora do assembly que compilado XAML precisa acessar um elemento XAML criado. Arquitetura de segurança do WPF junto com o comportamento de compilação XAML não declarar campos que armazenam instâncias de elemento como pública, a menos que você defina especificamente o `x:FieldModifier` para permitir acesso público.  
  
 `x:FieldModifier`só é relevante para elementos com um [diretiva X:Name](../../../docs/framework/xaml-services/x-name-directive.md) porque esse nome é usado para fazer referência ao campo depois que ele é público.  
  
 Por padrão, a classe parcial para o elemento raiz é pública; No entanto, você pode tornar confidenciais usando o [diretiva X:ClassModifier](../../../docs/framework/xaml-services/x-classmodifier-directive.md). O [diretiva X:ClassModifier](../../../docs/framework/xaml-services/x-classmodifier-directive.md) também afeta o nível de acesso da instância da classe de elemento raiz. Você pode colocar ambos `x:Name` e `x:FieldModifier` na raiz do elemento, mas isso só faz uma cópia de campo público do elemento raiz com true elemento classe acesso nível raiz ainda controlada por [diretiva X:ClassModifier](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Consulte também  
 [XAML e classes personalizadas para WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Code-behind e XAML no WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [Diretiva x:Name](../../../docs/framework/xaml-services/x-name-directive.md)  
 [Como compilar um aplicativo WPF (WPF)](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Diretiva x:ClassModifier](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
