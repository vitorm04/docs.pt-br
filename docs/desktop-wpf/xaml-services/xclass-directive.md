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
ms.openlocfilehash: 8f7ca5fdb170411aba24d34b8bf4d6c4f5776cc4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555140"
---
# <a name="xclass-directive"></a>Diretiva x:Class
Configura a compilação de marcação XAML para unir classes parciais entre marcação e code-behind. A classe parcial code é definida em um arquivo de código separado em uma linguagem Common Language Specification (CLS), enquanto a classe parcial de marcação normalmente é criada pela geração de código durante a compilação XAML.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`namespace`|Opcional. Especifica um namespace CLR que contém a classe parcial identificada por `classname` . Se `namespace` for especificado, um ponto (.) separa `namespace` e `classname` . Consulte Observações.|
|`classname`|Obrigatórios. Especifica o nome CLR da classe parcial que conecta o XAML carregado e seu code-behind para esse XAML.|

## <a name="dependencies"></a>Dependências

`x:Class` Só pode ser especificado no elemento raiz de uma produção XAML. `x:Class` é inválido em qualquer objeto que tenha um pai na produção XAML. Para obter mais informações, consulte [ \[ a \] seção MS-XAML 4.3.1.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Comentários

O `namespace` valor pode conter pontos adicionais para organizar namespaces relacionados em hierarquias de nomes, que é uma técnica comum na programação .net. Somente o último ponto em uma cadeia de caracteres de `x:Class` valores é interpretado para separado `namespace` e `classname.` a classe usada como `x:Class` não pode ser uma classe aninhada. Classes aninhadas não são permitidas porque determinar o significado de pontos para `x:Class` cadeias de caracteres é ambíguo se classes aninhadas são permitidas.

Em modelos de programação existentes que usam `x:Class` , `x:Class` é opcional no sentido de que ele é totalmente válido para ter uma página XAML sem code-behind. No entanto, essa funcionalidade interage com as ações de compilação conforme implementadas por estruturas que usam XAML. `x:Class` a funcionalidade também é influenciada pelas funções que várias classificações do conteúdo especificado pelo XAML têm em um modelo de aplicativo e nas ações de compilação correspondentes. Se o XAML declarar valores de atributo de manipulação de eventos ou instanciar elementos personalizados em que as classes de definição estão na classe code-behind, você precisa fornecer a `x:Class` referência de diretiva (ou [x:Subclass](xsubclass-directive.md)) à classe apropriada para code-behind.

O valor da `x:Class` diretiva deve ser uma cadeia de caracteres que especifica o nome totalmente qualificado de uma classe, mas sem nenhuma informação de assembly (equivalente a <xref:System.Type.FullName%2A?displayProperty=nameWithType> ). Para aplicativos simples, você pode omitir informações de namespace CLR se o code-behind também for estruturado dessa maneira (a definição de código começa no nível de classe).

O arquivo code-behind para uma definição de página ou aplicativo deve estar dentro de um arquivo de código que é incluído como parte do projeto que produz um aplicativo compilado e envolve a compilação de marcação. Você deve seguir as regras de nome para classes CLR. Para obter mais informações, consulte [diretrizes de design de estrutura](../../../api/index.md). Por padrão, a classe code-behind deve ser `public` ; no entanto, você pode defini-la em um nível de acesso diferente usando a [diretiva x:ClassModifier](xclassmodifier-directive.md).

Essa interpretação do `x:Class` atributo se aplica somente a uma implementação XAML baseada em CLR, em particular aos serviços XAML .net. Outras implementações de XAML que não são baseadas em CLR e que não usam os serviços XAML .NET podem usar uma fórmula de resolução diferente para conectar marcação XAML e fazer backup de código em tempo de execução. Para obter mais informações sobre interpretações mais gerais do `x:Class` , consulte [ \[ MS \] -XAML](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

Em um determinado nível de arquitetura, o significado de `x:Class` é indefinido nos serviços XAML .net. Isso ocorre porque os serviços XAML .NET não especificam o modelo de programação pelo qual a marcação XAML e o código de suporte estão conectados. Usos adicionais da `x:Class` diretiva podem ser implementados por estruturas específicas que usam modelos de programação ou modelos de aplicativo para definir como conectar marcação XAML e code-behind baseado em CLR. Cada estrutura pode ter suas próprias ações de compilação que habilitam Alguns dos comportamentos ou componentes específicos que devem ser incluídos no ambiente de compilação. Dentro de uma estrutura, as ações de compilação também podem variar dependendo da linguagem CLR específica que é usada para o code-behind.

## <a name="xclass-in-the-wpf-programming-model"></a>x:Class no modelo de programação do WPF

Em aplicativos do WPF e no modelo de aplicativo do WPF, `x:Class` pode ser declarado como um atributo para qualquer elemento que seja a raiz de um arquivo XAML e está sendo compilado (onde o XAML é incluído em um projeto de aplicativo do WPF com `Page` ação de compilação) ou para a <xref:System.Windows.Application> raiz na definição de aplicativo de um aplicativo WPF compilado. A Declaração `x:Class` em um elemento que não seja uma raiz de página ou de aplicativo, ou em um arquivo XAML WPF que não é compilado, causa um erro de tempo de compilação no compilador xaml .NET Framework 3,0 e .NET Framework 3,5 WPF. Para obter informações sobre outros aspectos de `x:Class` manipulação no WPF, consulte [code-behind e XAML no WPF](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf).

## <a name="xclass-for-windows-workflow-foundation"></a>x:Class para Windows Workflow Foundation
Por Windows Workflow Foundation, `x:Class` nomeia a classe de uma atividade personalizada composta inteiramente em XAML ou nomeia a classe parcial da página XAML para um designer de atividade com code-behind.

## <a name="silverlight-usage-notes"></a>Notas de uso do Silverlight

`x:Class` para o Silverlight é documentado separadamente. Para obter mais informações, consulte [XAML namespace (x:) Recursos de linguagem (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Confira também

- [Diretiva x:Subclass](xsubclass-directive.md)
- [XAML e classes personalizadas para WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
- [Diretiva x:ClassModifier](xclassmodifier-directive.md)
- [Tipos migrados do WPF para System.Xaml](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
