---
title: Diretiva x:Subclass
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d620b59208b9dc852abee3dd2e4d6c58b223d70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xsubclass-directive"></a>Diretiva x:Subclass
Modifica o comportamento de compilação de marcação XAML quando `x:Class` também é fornecido. Em vez de criar uma classe parcial que é baseada no `x:Class`, fornecido `x:Class` é criado como uma classe intermediária, e, em seguida, espera-se que a classe derivada fornecida seja baseada em `x:Class`.  
  
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
|`classname`|Necessário. Especifica o nome CLR da classe parcial que conecta o XAML carregado e o code-behind para esse XAML. Consulte Observações.|  
|`subclassNamespace`|Opcional. Pode ser diferente da `namespace` se cada namespace possa resolver o outro. Especifica um namespace CLR que contém `subclassName`. Se `subclassName` for especificado, um ponto (.) separa `subclassNamespace` e `subclassName`.|  
|`subclassName`|Necessário. Especifica o nome da subclasse do CLR.|  
  
## <a name="dependencies"></a>Dependências  
 [Diretiva X:Class](../../../docs/framework/xaml-services/x-class-directive.md) também deve ser fornecido no mesmo objeto, e esse objeto deve ser o elemento raiz de produção XAML.  
  
## <a name="remarks"></a>Comentários  
 `x:Subclass`uso destina-se principalmente a idiomas que não oferecem suporte a declarações de classe parcial.  
  
 A classe usada como o `x:Subclass` não pode ser uma classe aninhada, e `x:Subclass` devem se referir ao objeto raiz conforme explicado na seção "Dependências".  
  
 Caso contrário, o significado conceitual de `x:Subclass` não está definida por uma implementação de serviços XAML do .NET Framework. Isso ocorre porque o comportamento de serviços XAML do .NET Framework não especifica o modelo de programação geral pelo qual XAML marcação e código de backup estão conectados. Implementações de ainda mais os conceitos relacionados a `x:Class` e `x:Subclass` são executadas por estruturas específicas que usam modelos de programação ou modelos de aplicativo para definir como conectar-se a marcação XAML, marcação compilada e com base em CLR code-behind. Cada estrutura pode ter sua própria ações de compilação que permitem alguns comportamento ou componentes específicos que devem ser incluídos no ambiente de compilação. Em uma estrutura, ações de compilação também podem variar com base no idioma específico do CLR que é usado para o code-behind.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 `x:Subclass`pode ser em uma raiz de página ou no <xref:System.Windows.Application> raiz na definição de aplicativo, que já tenha `x:Class`. Declarando `x:Subclass` em qualquer elemento que não seja uma raiz de aplicativo ou página ou especificá-lo onde nenhum `x:Class` existe, causa um erro de tempo de compilação.  
  
 Criar classes derivadas que funcionam corretamente para o `x:Subclass` cenário é relativamente complexo. Talvez seja necessário examinar os arquivos intermediários (os arquivos. g produzidos na pasta obj do seu projeto pela compilação de marcação, com nomes que incorporam os nomes de arquivo. XAML). Esses arquivos intermediários podem ajudá-lo a determinar a origem de determinadas construções de programação nas classes parciais associadas no aplicativo compilado.  
  
 Manipuladores de eventos na classe derivada devem ser `internal override` (`Friend Overrides` em [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) para substituir os stubs para os manipuladores que foi criado na classe intermediária durante a compilação. Caso contrário, as implementações de classe derivada ocultar (sombra) a implementação da classe intermediária e manipuladores de classe intermediários não são invocados.  
  
 Quando você define tanto `x:Class` e `x:Subclass`, você não precisa fornecer qualquer implementação para a classe que é referenciada por `x:Class`. Você só precisa dar um nome por meio de `x:Class` atributo para que o compilador tenha alguma orientação para a classe que ele cria nos arquivos intermediários (o compilador não selecione um nome padrão neste caso). Você pode dar a `x:Class` uma implementação da classe; no entanto, isso não é o cenário típico para usar tanto `x:Class` e `x:Subclass`.  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva x:Class](../../../docs/framework/xaml-services/x-class-directive.md)  
 [XAML e classes personalizadas para WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
