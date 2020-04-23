---
title: Diretiva x:Subclass
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: e85e0fb5a0e1a865ed84a93767f8152a115bbe5f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071363"
---
# <a name="xsubclass-directive"></a>Diretiva x:Subclass

Modifica o comportamento de compilação `x:Class` de marcação XAML quando também é fornecido. Em vez de criar uma `x:Class`classe parcial `x:Class` baseada em , o fornecido é criado como uma classe intermediária, `x:Class`e então espera-se que sua classe derivada fornecida seja baseada em .

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`namespace`|Opcional. Especifica um namespace CLR `classname`que contenha . Se `namespace` for especificado, um dot `namespace` (.) separa e `classname`.|
|`classname`|Obrigatórios. Especifica o nome CLR da classe parcial que conecta o XAML carregado e o seu código-traseiro para esse XAML. Consulte Observações.|
|`subclassNamespace`|Opcional. Pode ser `namespace` diferente de se cada namespace pode resolver o outro. Especifica um namespace CLR `subclassName`que contenha . Se `subclassName` for especificado, um dot `subclassNamespace` (.) separa e `subclassName`.|
|`subclassName`|Obrigatórios. Especifica o nome CLR da subclasse.|

## <a name="dependencies"></a>Dependências

[x:Diretiva de classe](xclass-directive.md) também deve ser fornecida no mesmo objeto, e esse objeto deve ser o elemento raiz da produção XAML.

## <a name="remarks"></a>Comentários

`x:Subclass`o uso é destinado principalmente a idiomas que não suportam declarações parciais de classe.

A classe usada `x:Subclass` como não pode ser `x:Subclass` uma classe aninhada, e deve se referir ao objeto raiz conforme explicado na seção "Dependências".

Caso contrário, o `x:Subclass` significado conceitual de é indefinido por uma implementação de Serviços .NET XAML. Isso porque o comportamento do .NET XAML Services não especifica o modelo de programação global pelo qual a marcação XAML e o código de backup estão conectados. Implementações de outros `x:Class` conceitos `x:Subclass` relacionados e são realizadas por estruturas específicas que usam modelos de programação ou modelos de aplicativos para definir como conectar marcação XAML, marcação compilada e code-behind baseado em CLR. Cada estrutura pode ter suas próprias ações de construção que permitem alguns dos comportamentos, ou componentes específicos que devem ser incluídos no ambiente de construção. Dentro de uma estrutura, as ações de construção também podem variar de acordo com a linguagem CLR específica que é usada para o code-behind.

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

`x:Subclass`pode estar em uma raiz <xref:System.Windows.Application> de página ou na `x:Class`raiz na definição do aplicativo, que já tem . Declarar `x:Subclass` em qualquer elemento que não seja uma página ou `x:Class` raiz de aplicativo, ou especiá-lo onde não existe, causa um erro de tempo de compilação.

Criar classes derivadas que funcionem corretamente para o `x:Subclass` cenário é bastante complexo. Você pode precisar examinar os arquivos intermediários (os arquivos .g produzidos na pasta obj do seu projeto por compilação de marcação, com nomes que incorporam os nomes de arquivo .xaml). Esses arquivos intermediários podem ajudá-lo a determinar a origem de certos construtos de programação nas classes parciais unidas no aplicativo compilado.

Os manipuladores de eventos na `internal override` `Friend Overrides` classe derivada devem ser (no Microsoft Visual Basic) a fim de substituir os stubs para os manipuladores como criados na classe intermediária durante a compilação. Caso contrário, as implementações de classe derivadas ocultam (sombra) a implementação da classe intermediária e os manipuladores de classe intermediária não são invocados.

Quando você `x:Class` define `x:Subclass`ambos e , você não precisa fornecer qualquer `x:Class`implementação para a classe que é referenciada por . Você só precisa dar-lhe `x:Class` um nome através do atributo para que o compilador tenha alguma orientação para a classe que ele cria nos arquivos intermediários (o compilador não seleciona um nome padrão neste caso). Você pode `x:Class` dar à classe uma implementação; no entanto, este não é `x:Class` `x:Subclass`o cenário típico para o uso de ambos e .

## <a name="see-also"></a>Confira também

- [Diretiva x:Class](xclass-directive.md)
- [XAML e classes personalizadas para WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
