---
title: Estático
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: f020756466888f51298abb423997906ddc7caff7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350755"
---
# <a name="static-visual-basic"></a>Estático (Visual Basic)
Especifica que uma ou mais variáveis locais declaradas devem continuar a existir e manter seus valores mais recentes após o término do procedimento no qual elas são declaradas.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, uma variável local em um procedimento deixa de existir assim que o procedimento para. Uma variável estática continua existindo e retém seu valor mais recente. Na próxima vez em que o código chamar o procedimento, a variável não será reinicializada e ainda manterá o valor mais recente que você atribuiu a ela. Uma variável estática continua existindo durante o tempo de vida da classe ou do módulo em que ela está definida.  
  
## <a name="rules"></a>Regras  
  
- **Contexto de declaração.** Você pode usar `Static` apenas em variáveis locais. Isso significa que o contexto de declaração para uma variável `Static` deve ser um procedimento ou um bloco em um procedimento, e não pode ser um arquivo de origem, namespace, classe, estrutura ou módulo.  
  
     Você não pode usar `Static` dentro de um procedimento de estrutura.  
  
- Os tipos de dados de `Static` variáveis locais não podem ser inferidos. Para obter mais informações, consulte [inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
- **Modificadores combinados.** Não é possível especificar `Static` junto com `ReadOnly`, `Shadows`ou `Shared` na mesma declaração.  
  
## <a name="behavior"></a>Comportamento  
 Quando você declara uma variável estática em um procedimento `Shared`, apenas uma cópia da variável estática está disponível para o aplicativo inteiro. Você chama um procedimento de `Shared` usando o nome da classe, não uma variável que aponta para uma instância da classe.  
  
 Quando você declara uma variável estática em um procedimento que não é `Shared`, apenas uma cópia da variável está disponível para cada instância da classe. Você chama um procedimento não compartilhado usando uma variável que aponta para uma instância específica da classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso de `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 A variável de `Static` `totalSales` é inicializada como 0 somente uma vez. Cada vez que você inserir `updateSales`, `totalSales` ainda terá o valor mais recente que você calculou para ele.  
  
 O modificador de `Static` pode ser usado neste contexto:  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
- [Tempo de vida em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Declaração de Variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
