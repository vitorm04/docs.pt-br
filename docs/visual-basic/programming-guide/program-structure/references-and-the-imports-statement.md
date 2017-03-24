---
title: "Referências e a instrução Imports (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references, assembly
- namespaces, assemblies
- referencing assemblies
- Imports statement, referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 283a27e7703b31a9aeed8f7e4104e89b7ff78525
ms.lasthandoff: 03/13/2017

---
# <a name="references-and-the-imports-statement-visual-basic"></a>Referências e a instrução Imports (Visual Basic)
Você pode tornar externos objetos disponíveis para seu projeto, escolhendo o **adicionar referência** comando o **projeto** menu. Referências em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pode apontar para assemblies, que são como bibliotecas mas contêm mais informações.  
  
## <a name="the-imports-statement"></a>A instrução Imports  
 Módulos (assemblies) incluem um ou mais namespaces. Quando você adiciona uma referência a um assembly, você também pode adicionar uma `Imports` instrução em um módulo que controla a visibilidade dos namespaces daquele assembly dentro do módulo. O `Imports` instrução fornece um contexto de escopo que permite que você use apenas a parte do namespace necessária para fornecer uma referência única.  
  
 O `Imports` instrução tem a seguinte sintaxe:  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname`refere-se a um nome curto que você pode usar dentro de código para se referir a um namespace importado. `Namespace`é um namespace disponível através de uma referência de projeto, por meio de uma definição do projeto ou anterior `Imports` instrução.  
  
 Um módulo pode conter qualquer número de `Imports` instruções. Elas devem aparecer após qualquer `Option` instruções, se presente, mas antes de qualquer outro código.  
  
> [!NOTE]
>  Não confunda referências de projeto com o `Imports` instrução ou o `Declare` instrução. Referências de projeto tornam objetos externos, como objetos em assemblies, disponível para [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projetos. O `Imports` instrução é usada para simplificar o acesso às referências do projeto, mas não fornece acesso a esses objetos. O `Declare` instrução é usada para declarar uma referência a um procedimento externo em uma biblioteca de vínculo dinâmico (DLL).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Usando Aliases com a instrução Imports  
 O `Imports` instrução torna mais fácil acessar os métodos de classes, eliminando a necessidade de digitar explicitamente os nomes totalmente qualificados de referências. Os aliases permitem que você atribua um nome amigável a apenas uma parte de um namespace. Por exemplo, o retorno de carro/linha alimentação sequência que faz com que uma única parte do texto a ser exibido em várias linhas é parte do <xref:Microsoft.VisualBasic.ControlChars>módulo o <xref:Microsoft.VisualBasic?displayProperty=fullName>namespace.</xref:Microsoft.VisualBasic?displayProperty=fullName> </xref:Microsoft.VisualBasic.ControlChars> Para usar essa constante em um programa sem um alias, você precisa digitar o código a seguir:  
  
 [!code-vb[VbVbalrApplication n º&3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports`instruções devem sempre ser as primeiras linhas imediatamente após quaisquer `Option` instruções em um módulo. O fragmento de código a seguir mostra como importar e atribuir um alias para o <xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>módulo:</xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>  
  
 [!code-vb[VbVbalrApplication n º&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 Referências futuras a esse namespace podem ser consideravelmente menores:  
  
 [!code-vb[VbVbalrApplication n º&5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 Se um `Imports` instrução não incluir um nome de alias, elementos definidos no namespace importado podem ser usados no módulo sem qualificação. Se o nome do alias for especificado, ele deve ser usado como um qualificador para nomes contidos naquele namespace.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ControlChars></xref:Microsoft.VisualBasic.ControlChars>   
 <xref:Microsoft.VisualBasic></xref:Microsoft.VisualBasic>   
 [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Como: criar e usar Assemblies usando a linha de comando](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)   
 [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
