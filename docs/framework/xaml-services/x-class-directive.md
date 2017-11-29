---
title: Diretiva x:Class
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 1828ef3614cc1f3a81d8aeff62c15ed5accfe380
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xclass-directive"></a>Diretiva x:Class
Configura a compilação da marcação XAML para unir classes parciais entre marcação e código. A classe código parcial é definida em um arquivo de código separado em um [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] idioma, enquanto a classe parcial da marcação é geralmente criada por geração de código durante a compilação de XAML.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`namespace`|Opcional. Especifica um [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] namespace que contém as classes parciais identificadas por `classname`. Se `namespace` for especificado, um ponto (.) separa `namespace` e `classname`. Consulte Observações.|  
|`classname`|Necessário. Especifica o [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] nome da classe parcial que conecta o XAML carregado e o code-behind para esse XAML.|  
  
## <a name="dependencies"></a>Dependências  
 `x:Class`só pode ser especificada no elemento raiz de uma produção XAML. `x:Class`é inválido em qualquer objeto que tem um pai na produção XAML. Para obter mais informações, consulte [ \[XAML MS\] seção 4.3.1.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Comentários  
 O `namespace` valor pode conter pontos adicionais para organizar dos namespaces relacionados em hierarquias de nome, que é uma técnica comum na programação do .NET Framework. O último ponto em uma cadeia de caracteres de `x:Class` é interpretado como valores separados `namespace` e `classname.` a classe é usada como `x:Class` não pode ser uma classe aninhada. Classes aninhadas não são permitidas porque a determinar o significado de pontos para `x:Class` cadeias de caracteres é ambíguo se são permitidas classes aninhadas.  
  
 Existente que usam modelos de programação `x:Class`, `x:Class` é opcional no sentido de que é totalmente válido para que uma página XAML com nenhum código subjacente. No entanto, esse recurso interage com as ações de compilação, conforme implementado pela estruturas que usam XAML. `x:Class`recurso também é influenciado por funções que várias classificações de conteúdo XAML especificado tem em um modelo de aplicativo e nas ações de construção. Se seu XAML declara instancia elementos personalizados onde as classes definidas são na classe code-behind ou valores de atributo de manipulação de eventos, você precisa fornecer o `x:Class` diretiva referência (ou [X:Subclass](../../../docs/framework/xaml-services/x-subclass-directive.md)) para o classe apropriada para code-behind.  
  
 O valor da `x:Class` diretiva deve ser uma cadeia de caracteres que especifica o nome totalmente qualificado de uma classe, mas sem qualquer informação de assembly (equivalente a <xref:System.Type.FullName%2A?displayProperty=nameWithType>). Aplicativos simples, você pode omitir as informações do namespace CLR se code-behind também é estruturado dessa maneira (início de definição de código no nível de classe).  
  
 O arquivo code-behind para uma definição de aplicativo ou página deve estar dentro de um arquivo de código que é incluído como parte do projeto que produz um aplicativo compilado e envolve a compilação da marcação. Você deve seguir as regras de nomeação para classes CLR. Para obter mais informações, consulte [diretrizes de Design do Framework](../../../docs/standard/design-guidelines/index.md). Por padrão, a classe code-behind deve ser `public`; no entanto, você pode defini-la em um nível de acesso diferente usando o [diretiva X:ClassModifier](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
 Essa interpretação de `x:Class` atributo só se aplica a uma implementação de XAML baseado em CLR, em particular para serviços XAML do .NET Framework. Outras implementações de XAML que não são baseados em CLR e que não usam serviços XAML do .NET Framework podem usar uma fórmula de uma resolução diferente para conectar-se a marcação XAML e fazendo o código de tempo de execução. Para obter mais informações sobre interpretações mais gerais de `x:Class`, consulte [ \[XAML MS\]](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 Em um determinado nível de arquitetura, o significado de `x:Class` não está definida nos serviços de XAML do .NET Framework. Isso ocorre porque os serviços de XAML do .NET Framework não especifica o modelo de programação pelo qual XAML marcação e código de backup estão conectados. Usos adicionais do `x:Class` diretiva pode ser implementada por estruturas específicas que usam modelos de programação ou modelos de aplicativo para definir como conectar-se a marcação XAML e baseado em CLR code-behind. Cada estrutura pode ter sua própria ações de compilação que permitem alguns dos componentes específicos que devem ser incluídos no ambiente de compilação ou comportamento. Em uma estrutura, as ações de compilação também podem variar dependendo da linguagem CLR específica que é usada para o code-behind.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>X:Class no modelo de programação do WPF  
 Em aplicativos do WPF e do modelo de aplicativo do WPF, `x:Class` pode ser declarado como um atributo de qualquer elemento que é a raiz de um arquivo XAML e está sendo compilado (onde o XAML está incluído em um projeto de aplicativo do WPF com `Page` ação de compilação), ou para o < C4 > <xref:System.Windows.Application>  raiz na definição de aplicativo de um aplicativo WPF compilado. Declarando `x:Class` em um elemento que não seja uma raiz de página ou a raiz do aplicativo, ou em um arquivo XAML WPF que não está compilado, causa um erro de tempo de compilação sob o [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] e [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] compilador WPF XAML. Para obter informações sobre outros aspectos do `x:Class` tratamento em WPF, consulte [Code-Behind e XAML no WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>X:Class para Windows Workflow Foundation  
 Para Windows Workflow Foundation, `x:Class` nomes de classe de uma atividade personalizada composta inteiramente em XAML ou nomes de classe parcial da página XAML para um designer de atividade com code-behind.  
  
## <a name="silverlight-usage-notes"></a>Observações de uso do Silverlight  
 `x:Class`para o Silverlight é documentado separadamente. Para obter mais informações, consulte [Namespace XAML (x) Recursos de linguagem (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva x:Subclass](../../../docs/framework/xaml-services/x-subclass-directive.md)  
 [XAML e classes personalizadas para WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Diretiva x:ClassModifier](../../../docs/framework/xaml-services/x-classmodifier-directive.md)  
 [Tipos migrados do WPF para System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
