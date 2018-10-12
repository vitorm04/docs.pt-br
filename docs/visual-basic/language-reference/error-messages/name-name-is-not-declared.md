---
title: Nome &#39; &lt;nome&gt; &#39; não está declarado
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
author: rpetrusha
ms.author: ronpet
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 3f950bd5604fae7c7d48f6898a4514053061fe10
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49122793"
---
# <a name="name-39ltnamegt39-is-not-declared"></a>Nome &#39; &lt;nome&gt; &#39; não está declarado
Uma declaração se refere a um elemento de programação, mas o compilador não pode localizar um elemento com esse nome exato.  
  
 **ID do erro:** BC30451  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique a ortografia do nome na declaração de referência. Visual Basic diferencia maiusculas de minúsculas, mas qualquer outra variação de grafia é considerada como um nome completamente diferente. Observe que o caractere de sublinhado (`_`) é parte do nome e, portanto, parte da ortografia.  
  
2. Verifique se você tem o operador de acesso de membro (`.`) entre um objeto e seus membros. Por exemplo, se você tiver um <xref:System.Windows.Forms.TextBox> controle chamado `TextBox1`, para acessar seus <xref:System.Windows.Forms.TextBoxBase.Text%2A> propriedade, você deve digitar `TextBox1.Text`. Se, em vez disso, você digita `TextBox1Text`, você criou um nome diferente.  
  
3. Se a ortografia está correta e a sintaxe de qualquer acesso de membro de objeto está correta, verifique se que o elemento foi declarado. Para obter mais informações, consulte [elementos declarados](../../programming-guide/language-features/declared-elements/index.md).  
  
4. Se o elemento de programação tiver sido declarado, verifique se ele está no escopo. Se a referência está fora da região que declara o elemento de programação, você precisa qualificar o nome do elemento. Para obter mais informações, consulte [escopo no Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).  

5. Se você não estiver usando um tipo totalmente qualificado ou o nome de tipo e membro (por exemplo, seu código fizer referência a uma propriedade como `MethodInfo.Name` em vez de `System.Reflection.MethodInfo.Name`), adicione um [instrução Imports](../statements/imports-statement-net-namespace-and-type.md).

6. Se você está tentando compilar um projeto de estilo do SDK (um projeto com um \*arquivo. vbproj que começa com a linha `<Project Sdk="Microsoft.NET.Sdk">`) e a mensagem de erro se refere a um tipo ou membro no assembly VisualBasic, configurar seu aplicativo para Compile com uma referência à biblioteca de tempo de execução do Visual Basic. Por padrão, um subconjunto da biblioteca é inserido em seu assembly em um projeto de estilo do SDK.

   Por exemplo, o exemplo a seguir falhará ao ser compilado porque o <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> método não pode ser encontrado. Ele não será inserido no subconjunto do Runtime do Visual Basic, incluído com o seu aplicativo.  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb)]

   Para resolver esse erro, adicione a `<VBRuntime>Default</VBRuntime>` elemento aos projetos `<PropertyGroup>` seção, como a seguir de arquivo de projeto do Visual Basic.

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a>Consulte também  

[Resumo de Declarações e Constantes](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Nomes de Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
