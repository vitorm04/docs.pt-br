---
title: Diretiva x:Class
ms.date: 03/30/2017
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
ms.openlocfilehash: ee94d7bf52f3fb2ea534cdb2f44d0be2cc8699eb
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689407"
---
# <a name="xclass-directive"></a>Diretiva x:Class
Configura a compilação de marcação XAML para ingressar em classes parciais entre marcação e code-behind. A classe código parcial é definida em um arquivo de código separado em um [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] idioma, enquanto a classe parcial de marcação é normalmente criada pela geração de código durante a compilação de XAML.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`namespace`|Opcional. Especifica um [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] namespace que contém as classes parciais identificadas pelo `classname`. Se `namespace` for especificado, um ponto (.) separa `namespace` e `classname`. Consulte Observações.|  
|`classname`|Necessário. Especifica o [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] nome da classe parcial que conecta o XAML carregado e o code-behind para esse XAML.|  
  
## <a name="dependencies"></a>Dependências  
 `x:Class` só pode ser especificado no elemento raiz de uma produção de XAML. `x:Class` é inválido em qualquer objeto que tem um pai na produção de XAML. Para obter mais informações, consulte [ \[MS-XAML\] seção 4.3.1.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Comentários  
 O `namespace` valor pode conter pontos adicionais para organizar os namespaces relacionados em hierarquias de nome, que é uma técnica comum na programação do .NET Framework. O último ponto em uma cadeia de caracteres `x:Class` valores é interpretado como para separar `namespace` e `classname.` a classe que é usada como `x:Class` não pode ser uma classe aninhada. Classes aninhadas não são permitidas porque a determinar o significado dos pontos para `x:Class` cadeias de caracteres é ambíguo se classes aninhadas são permitidas.  
  
 Existente que usam modelos de programação `x:Class`, `x:Class` é opcional no sentido de que ele é totalmente válido para ter uma página XAML que não tem nenhum code-behind. No entanto, esse recurso interage com as ações de compilação conforme implementado pela estruturas que usam XAML. `x:Class` recurso também é influenciado pelas funções que várias classificações de conteúdo especificada pelo XAML tem em um modelo de aplicativo e ações de build nas correspondentes. Se seu XAML declara instancia elementos personalizados onde as classes definidas são na classe code-behind ou valores de atributo de manipulação de eventos, você precisará fornecer as `x:Class` referência de diretiva (ou [X:Subclass](x-subclass-directive.md)) para o classe apropriada para code-behind.  
  
 O valor da `x:Class` diretiva deve ser uma cadeia de caracteres que especifica o nome totalmente qualificado de uma classe, mas sem qualquer informação de assembly (equivalente ao <xref:System.Type.FullName%2A?displayProperty=nameWithType>). Para aplicativos simples, você pode omitir informações de namespace CLR, se o code-behind também é estruturado dessa maneira (inícios de definição de código no nível de classe).  
  
 O arquivo code-behind para uma definição de página ou do aplicativo deve estar dentro de um arquivo de código que é incluído como parte do projeto que produz um aplicativo compilado e envolve a compilação de marcação. Você deve seguir as regras de nomeação para classes CLR. Para obter mais informações, consulte [diretrizes de Design do Framework](../../standard/design-guidelines/index.md). Por padrão, a classe code-behind deve ser `public`; no entanto, você pode defini-la em um nível de acesso diferente usando o [diretiva X:ClassModifier](x-classmodifier-directive.md).  
  
 Essa interpretação do `x:Class` atributo se aplica somente a uma implementação de XAML baseado em CLR, em particular para serviços de XAML do .NET Framework. Outras implementações de XAML que não são baseados em CLR e que não usam serviços de XAML do .NET Framework podem usar uma fórmula de uma resolução diferente para conectar-se a marcação XAML e fazer o código de tempo de execução. Para obter mais informações sobre a interpretações mais gerais sobre `x:Class`, consulte [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
 Em um determinado nível da arquitetura, o significado de `x:Class` não está definida nos serviços de XAML do .NET Framework. Isso ocorre porque os serviços de XAML do .NET Framework não especifica o modelo de programação pelo qual XAML marcação e código de backup estão conectados. Usos adicionais do `x:Class` diretiva pode ser implementada por estruturas específicas que usam modelos de programação ou modelos de aplicativo para definir como se conectar a marcação XAML e code-behind com base em CLR. Cada estrutura pode ter suas próprias ações de compilação que permitem que alguns dos componentes específicos que devem ser incluídos no ambiente de compilação ou comportamento. Dentro de uma estrutura, as ações de build também podem variar dependendo da linguagem específica do CLR que é usada para o code-behind.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>X:Class no modelo de programação do WPF  
 Em aplicativos WPF e o modelo de aplicativo do WPF `x:Class` pode ser declarado como um atributo para qualquer elemento que é a raiz de um arquivo XAML e está sendo compilado (onde o XAML está incluído em um projeto de aplicativo do WPF com `Page` ação de build), ou para o < C4 > <xref:System.Windows.Application>  raiz na definição de aplicativo de um aplicativo WPF compilado. Declarando `x:Class` em um elemento diferente de raiz da página ou a raiz do aplicativo, ou em um arquivo XAML WPF que não seja compilado, causa um erro de tempo de compilação sob o [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] e o compilador do .NET Framework 3.5 WPF XAML. Para obter informações sobre outros aspectos da `x:Class` tratamento no WPF, consulte [Code-Behind e XAML no WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>X:Class for Windows Workflow Foundation  
 Para o Windows Workflow Foundation, `x:Class` nomeia a classe de uma atividade personalizada composta inteiramente em XAML ou nomes de classe parcial da página XAML para um designer de atividade com code-behind.  
  
## <a name="silverlight-usage-notes"></a>Notas de uso do Silverlight  
 `x:Class` para o Silverlight está documentado separadamente. Para obter mais informações, consulte [Namespace de XAML (x) Recursos de linguagem (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Consulte também

- [Diretiva x:Subclass](x-subclass-directive.md)
- [XAML e classes personalizadas para WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Diretiva x:ClassModifier](x-classmodifier-directive.md)
- [Tipos migrados do WPF para System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
