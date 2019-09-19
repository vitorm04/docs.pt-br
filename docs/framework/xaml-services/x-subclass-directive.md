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
ms.openlocfilehash: f6f02998a7648693bd731d6b2afdfd4499abaa04
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053907"
---
# <a name="xsubclass-directive"></a>Diretiva x:Subclass
Modifica o comportamento de compilação de marcação `x:Class` XAML quando também é fornecido. Em vez de criar uma classe parcial baseada em `x:Class`, a fornecida `x:Class` é criada como uma classe intermediária e, em seguida, a classe derivada fornecida deve se basear `x:Class`.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`namespace`|Opcional. Especifica um namespace CLR que contém `classname`. Se `namespace` for especificado, um ponto (.) `namespace` separa e `classname`.|  
|`classname`|Necessário. Especifica o nome CLR da classe parcial que conecta o XAML carregado e seu code-behind para esse XAML. Consulte Observações.|  
|`subclassNamespace`|Opcional. Pode ser diferente de `namespace` se cada namespace puder resolver o outro. Especifica um namespace CLR que contém `subclassName`. Se `subclassName` for especificado, um ponto (.) `subclassNamespace` separa e `subclassName`.|  
|`subclassName`|Necessário. Especifica o nome CLR da subclasse.|  
  
## <a name="dependencies"></a>Dependências  
 a [diretiva x:Class](x-class-directive.md) também deve ser fornecida no mesmo objeto e esse objeto deve ser o elemento raiz da produção XAML.  
  
## <a name="remarks"></a>Comentários  
 `x:Subclass`o uso destina-se principalmente a linguagens que não dão suporte a declarações de classe parciais.  
  
 A classe usada como `x:Subclass` não pode ser uma classe aninhada e `x:Subclass` deve se referir ao objeto raiz, conforme explicado na seção "dependências".  
  
 Caso contrário, o significado conceitual do `x:Subclass` é indefinido por uma implementação de serviços XAML .NET Framework. Isso ocorre porque .NET Framework comportamento dos serviços XAML não especifica o modelo de programação geral pelo qual a marcação XAML e o código de suporte estão conectados. Implementações de outros conceitos relacionados `x:Class` ao `x:Subclass` e são executadas por estruturas específicas que usam modelos de programação ou modelos de aplicativos para definir como conectar marcação XAML, marcação compilada e code-behind baseado em CLR. Cada estrutura pode ter suas próprias ações de compilação que habilitam parte do comportamento ou componentes específicos que devem ser incluídos no ambiente de compilação. Dentro de uma estrutura, as ações de compilação também podem variar com base na linguagem CLR específica que é usada para o code-behind.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 `x:Subclass`pode estar em uma raiz de página ou na <xref:System.Windows.Application> raiz na definição do aplicativo, que já tem `x:Class`. Declarar `x:Subclass` em qualquer elemento que não seja uma página ou raiz do aplicativo, ou especificá `x:Class` -lo onde não exista, causa um erro em tempo de compilação.  
  
 Criar classes derivadas que funcionam corretamente para o `x:Subclass` cenário é razoavelmente complexo. Talvez seja necessário examinar os arquivos intermediários (os arquivos. g produzidos na pasta obj do projeto por compilação de marcação, com nomes que incorporam os nomes de arquivo. XAML). Esses arquivos intermediários podem ajudá-lo a determinar a origem de determinadas construções de programação nas classes parciais Unidas no aplicativo compilado.  
  
 Manipuladores de eventos na classe derivada devem ser `internal override` (`Friend Overrides` no Microsoft Visual Basic) para substituir os stubs para os manipuladores conforme criados na classe intermediária durante a compilação. Caso contrário, as implementações de classe derivada ocultam (Shadow) a implementação da classe intermediária e os manipuladores de classe intermediários não são invocados.  
  
 Quando você define `x:Class` e `x:Subclass`, não é necessário fornecer nenhuma implementação para a classe que é referenciada pelo `x:Class`. Você só precisa dar a ele um nome por meio `x:Class` do atributo para que o compilador tenha alguma orientação para a classe que ele cria nos arquivos intermediários (o compilador não seleciona um nome padrão nesse caso). Você pode dar uma `x:Class` implementação à classe; no entanto, esse não é o cenário típico para `x:Class` usar `x:Subclass`o e o.  
  
## <a name="see-also"></a>Consulte também

- [Diretiva x:Class](x-class-directive.md)
- [XAML e classes personalizadas para WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
