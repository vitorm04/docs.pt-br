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
ms.openlocfilehash: f589fa70c2ee1c56544fa0f0152990478aa3761f
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072035"
---
# <a name="xclass-directive"></a>Diretiva x:Class
Configura a compilação de marcação XAML para participar de classes parciais entre marcação e código atrás. A classe parcial de código é definida em um arquivo de código separado em uma linguagem DE Especificação de Linguagem Comum (CLS), enquanto a classe parcial de marcação é tipicamente criada pela geração de código durante a compilação XAML.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`namespace`|Opcional. Especifica um namespace CLR que contém `classname`a classe parcial identificada por . Se `namespace` for especificado, um dot `namespace` (.) separa e `classname`. Consulte Observações.|
|`classname`|Obrigatórios. Especifica o nome CLR da classe parcial que conecta o XAML carregado e o seu código-traseiro para esse XAML.|

## <a name="dependencies"></a>Dependências

`x:Class`só pode ser especificado no elemento raiz de uma produção XAML. `x:Class`é inválido em qualquer objeto que tenha um pai na produção XAML. Para obter mais informações, consulte [ \[\] MS-XAML Seção 4.3.1.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Comentários

O `namespace` valor pode conter outros pontos para organizar namespaces relacionados em hierarquias de nomes, que é uma técnica comum na programação .NET. Apenas o último dot `x:Class` em uma seqüência de valores é interpretado para separar `namespace` e `classname.` a classe que é usada como `x:Class` não pode ser uma classe aninhada. Classes aninhadas não são permitidas porque `x:Class` determinar o significado de dosts para strings é ambíguo se classes aninhadas forem permitidas.

Nos modelos de programação `x:Class` `x:Class` existentes que usam, é opcional no sentido de que é totalmente válido ter uma página XAML que não tenha código atrás. No entanto, esse recurso interage com as ações de construção implementadas por frameworks que usam XAML. `x:Class`o recurso também é influenciado pelas funções que várias classificações de conteúdo especificado por XAML têm em um modelo de aplicativo e nas ações de compilação correspondentes. Se o XAML declarar valores de atributo de manipulação de eventos ou instanciar elementos `x:Class` personalizados onde as classes definidoras estão na classe de código atrás, você terá que fornecer a referência diretiva (ou [x:Subclasse)](xsubclass-directive.md)à classe apropriada para o code-behind.

O valor `x:Class` da diretiva deve ser uma string que especifica o nome totalmente qualificado <xref:System.Type.FullName%2A?displayProperty=nameWithType>de uma classe, mas sem qualquer informação de montagem (equivalente à ). Para aplicações simples, você pode omiti-lo informações de namespace da CLR se o code-behind também estiver estruturado dessa maneira (a definição de código começa no nível de classe).

O arquivo de código atrás para uma definição de página ou aplicativo deve estar dentro de um arquivo de código que está incluído como parte do projeto que produz um aplicativo compilado e envolve compilação de marcação. Você deve seguir as regras de nome para as aulas de CLR. Para obter mais informações, consulte [Framework Design Guidelines](../../../api/index.md). Por padrão, a classe de `public`código atrás deve ser; no entanto, você pode defini-lo em um nível de acesso diferente usando a [diretiva x:ClassModifier](xclassmodifier-directive.md).

Essa interpretação `x:Class` do atributo se aplica apenas a uma implementação XAML baseada em CLR, em particular aos Serviços .NET XAML. Outras implementações XAML que não são baseadas em CLR e que não usam .NET XAML Services podem usar uma fórmula de resolução diferente para conectar a marcação XAML e o código de tempo de execução de backup. Para obter mais informações sobre `x:Class`interpretações mais gerais de , consulte [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

Em um certo nível de `x:Class` arquitetura, o significado de é indefinido em .NET XAML Services. Isso porque o .NET XAML Services não especifica o modelo de programação pelo qual a marcação XAML e o código de backup estão conectados. Usos adicionais da `x:Class` diretiva podem ser implementados por estruturas específicas que usam modelos de programação ou modelos de aplicativos para definir como conectar a marcação XAML e o code-behind baseado em CLR. Cada estrutura pode ter suas próprias ações de construção que permitem alguns dos comportamentos ou componentes específicos que devem ser incluídos no ambiente de construção. Dentro de uma estrutura, as ações de construção também podem variar dependendo da linguagem CLR específica que é usada para o code-behind.

## <a name="xclass-in-the-wpf-programming-model"></a>x:Classe no modelo de programação WPF

Em aplicativos WPF e no modelo `x:Class` de aplicativo WPF, pode ser declarado como um atributo para qualquer elemento que seja a raiz de um `Page` arquivo XAML <xref:System.Windows.Application> e está sendo compilado (onde o XAML é incluído em um projeto de aplicativo WPF com ação de compilação), ou para a raiz na definição de aplicativo de um aplicativo WPF compilado. Declarar `x:Class` em um elemento que não seja uma raiz de página ou raiz de aplicativo, ou em um arquivo WPF XAML que não é compilado, causa um erro de tempo de compilação sob o compilador .NET Framework 3.0 e .NET Framework 3.5 WPF XAML. Para obter informações sobre `x:Class` outros aspectos do manuseio no WPF, consulte [Code-Behind e XAML em WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

## <a name="xclass-for-windows-workflow-foundation"></a>x:Class for Windows Workflow Foundation
Para o Windows `x:Class` Workflow Foundation, nomeia a classe de uma atividade personalizada composta inteiramente em XAML, ou nomeia a classe parcial da página XAML para um designer de atividades com código atrás.

## <a name="silverlight-usage-notes"></a>Notas de uso da luz de prata

`x:Class`para Silverlight é documentado separadamente. Para obter mais informações, consulte [XAML Namespace (x:) Características da linguagem (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Confira também

- [Diretiva x:Subclass](xsubclass-directive.md)
- [XAML e classes personalizadas para WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Diretiva x:ClassModifier](xclassmodifier-directive.md)
- [Tipos migrados do WPF para System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
