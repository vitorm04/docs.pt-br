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
ms.openlocfilehash: 850fe8acf9e47149bd385e78b30e04ba77d7a8b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938860"
---
# <a name="xsubclass-directive"></a>Diretiva x:Subclass
Modifica o comportamento de compilação de marcação XAML quando `x:Class` também é fornecido. Em vez de criar uma classe parcial que se baseia `x:Class`, fornecido `x:Class` é criado como uma classe intermediária, e, em seguida, sua classe derivada fornecido deve ser baseada em `x:Class`.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`namespace`|Opcional. Especifica um namespace CLR que contém `classname`. Se `namespace` for especificado, um ponto (.) separa `namespace` e `classname`.|  
|`classname`|Necessário. Especifica o nome da classe parcial que conecta o XAML carregado e o code-behind para esse XAML do CLR. Consulte Observações.|  
|`subclassNamespace`|Opcional. Pode ser diferente da `namespace` se cada namespace pode resolver o outro. Especifica um namespace CLR que contém `subclassName`. Se `subclassName` for especificado, um ponto (.) separa `subclassNamespace` e `subclassName`.|  
|`subclassName`|Necessário. Especifica o nome da subclasse do CLR.|  
  
## <a name="dependencies"></a>Dependências  
 [Diretiva X:Class](x-class-directive.md) também deve ser fornecido no mesmo objeto, e esse objeto deve ser o elemento raiz da produção de XAML.  
  
## <a name="remarks"></a>Comentários  
 `x:Subclass` uso destina-se principalmente a idiomas que não dão suporte a declarações de classe parcial.  
  
 A classe usada como o `x:Subclass` não pode ser uma classe aninhada, e `x:Subclass` deve se referir ao objeto raiz conforme explicado na seção "Dependências".  
  
 Caso contrário, o significado conceitual de `x:Subclass` não está definida por uma implementação de serviços de XAML do .NET Framework. Isso ocorre porque o comportamento de serviços de XAML do .NET Framework não especifica o modelo de programação geral pelo qual XAML marcação e código de backup estão conectados. Implementações de ainda mais os conceitos relacionados ao `x:Class` e `x:Subclass` são executadas por estruturas específicas que usam modelos de programação ou modelos de aplicativo para definir como se conectar a marcação XAML, o marcação compilada e o code-behind com base em CLR. Cada estrutura pode ter suas próprias ações de compilação que permitem alguns comportamento ou componentes específicos que devem ser incluídos no ambiente de compilação. Dentro de uma estrutura, as ações de build também podem variar com base na linguagem específica de CLR que é usada para o code-behind.  
  
## <a name="wpf-usage-notes"></a>Notas de uso do WPF  
 `x:Subclass` pode ser em uma raiz de página ou nos <xref:System.Windows.Application> raiz na definição de aplicativo, que já tem `x:Class`. Declarando `x:Subclass` em qualquer elemento que não seja uma raiz de página ou do aplicativo ou especificá-lo onde não `x:Class` existe, causa um erro de tempo de compilação.  
  
 Criar classes derivadas que funcionam corretamente para o `x:Subclass` cenário é bastante complexo. Talvez seja necessário examinar os arquivos intermediários (os arquivos. g produzidos na pasta obj do projeto por compilação de marcação, com nomes que incorporam os nomes de arquivo. XAML). Esses arquivos intermediários podem ajudá-lo a determinar a origem de determinadas construções de programação em classes parciais associadas no aplicativo compilado.  
  
 Manipuladores de eventos na classe derivada devem ser `internal override` (`Friend Overrides` no Microsoft Visual Basic) para substituir os stubs para os manipuladores como criada na classe intermediária durante a compilação. Caso contrário, as implementações de classe derivada ocultar (sombra) a implementação da classe intermediária e manipuladores de classe intermediários não são invocados.  
  
 Quando você define tanto `x:Class` e `x:Subclass`, você não precisa fornecer qualquer implementação para a classe que é referenciada por `x:Class`. Você só precisa nomeá-lo por meio de `x:Class` de atributo para que o compilador tem algumas diretrizes para a classe que ele cria nos arquivos intermediários (o compilador não selecione um nome padrão neste caso). Você pode dar a `x:Class` uma implementação da classe; no entanto, isso não é o cenário típico para usar ambos `x:Class` e `x:Subclass`.  
  
## <a name="see-also"></a>Consulte também

- [Diretiva x:Class](x-class-directive.md)
- [XAML e classes personalizadas para WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
