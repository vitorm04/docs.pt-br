---
title: Instrução Module (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 08268fd473a3a916f41f2f46090e3245acda07dd
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513003"
---
# <a name="module-statement"></a>Instrução Module
Declara o nome de um módulo e apresenta a definição das variáveis, propriedades, eventos e procedimentos que o módulo compreende.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a>Partes  
 `attributelist`  
 Opcional. Consulte a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Opcional. Pode ser um dos seguintes:  
  
- [Público](../../../visual-basic/language-reference/modifiers/public.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `name`  
 Necessário. Nome deste módulo. Consulte [nomes de elementos](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)declarados.  
  
 `statements`  
 Opcional. Instruções que definem as variáveis, propriedades, eventos, procedimentos e tipos aninhados deste módulo.  
  
 `End Module`  
 Encerra a `Module` definição.  
  
## <a name="remarks"></a>Comentários  
 Uma `Module` instrução define um tipo de referência disponível em todo o namespace. Um *módulo* (às vezes chamado de *módulo padrão*) é semelhante a uma classe, mas com algumas distinções importantes. Cada módulo tem exatamente uma instância e não precisa ser criado ou atribuído a uma variável. Os módulos não dão suporte à herança ou à implementação de interfaces. Observe que um módulo não é um *tipo* no sentido de que uma classe ou estrutura é — você não pode declarar um elemento de programação para ter o tipo de dados de um módulo.  
  
 Você pode usar `Module` somente no nível de namespace. Isso significa que o *contexto de declaração* para um módulo deve ser um arquivo ou namespace de origem e não pode ser uma classe, estrutura, módulo, interface, procedimento ou bloco. Não é possível aninhar um módulo dentro de outro módulo ou dentro de qualquer tipo. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Um módulo tem o mesmo tempo de vida do seu programa. Como seus membros são todos `Shared`, eles também têm tempos de vida iguais aos do programa.  
  
 Os módulos são padrão para acesso [Friend](../../../visual-basic/language-reference/modifiers/friend.md) . Você pode ajustar seus níveis de acesso com os modificadores de acesso. Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Todos os membros de um módulo são implicitamente `Shared`.  
  
## <a name="classes-and-modules"></a>Classes e módulos  
 Esses elementos têm muitas semelhanças, mas também há algumas diferenças importantes.  
  
- **Terminologia.** As versões anteriores do Visual Basic reconhecem dois tipos de módulos: *módulos de classe* (arquivos. CLS) e *módulos padrão* (arquivos. bas). A versão atual chama essas *classes* e *módulos*, respectivamente.  
  
- **Membros compartilhados.** Você pode controlar se um membro de uma classe é um membro compartilhado ou de instância.  
  
- **Orientação do objeto.** As classes são orientadas a objeto, mas os módulos não são. Portanto, somente classes podem ser instanciadas como objetos. Para obter mais informações, consulte [objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="rules"></a>Regras  
  
- **Modificadores.** Todos os membros do módulo são [compartilhados](../../../visual-basic/language-reference/modifiers/shared.md)implicitamente. Você não pode usar `Shared` a palavra-chave ao declarar um membro e não pode alterar o status compartilhado de nenhum membro.  
  
- **Herança.** Um módulo não pode herdar de nenhum tipo <xref:System.Object>diferente de, do qual todos os módulos herdam. Em particular, um módulo não pode herdar de outro.  
  
     Você não pode usar a [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) em uma definição de módulo, <xref:System.Object>até mesmo para especificar.  
  
- **Propriedade padrão.** Você não pode definir nenhuma propriedade padrão em um módulo. Para obter mais informações, consulte [padrão](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Comportamento  
  
- **Nível de acesso.** Dentro de um módulo, você pode declarar cada membro com seu próprio nível de acesso. Os membros do módulo assumem como padrão acesso [público](../../../visual-basic/language-reference/modifiers/public.md) , Exceto variáveis e constantes, que assumem como padrão o acesso [privado](../../../visual-basic/language-reference/modifiers/private.md) . Quando um módulo tem acesso mais restrito do que um de seus membros, o nível de acesso do módulo especificado tem precedência.  
  
- **Com.** Um módulo está no escopo em todo o namespace.  
  
     O escopo de cada membro de módulo é o módulo inteiro. Observe que todos os membros sofrem a *promoção de tipos*, o que faz com que seu escopo seja promovido para o namespace que contém o módulo. Para obter mais informações, consulte [promoção de tipos](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
- **Aprovação.** Você pode ter vários módulos em um projeto e pode declarar membros com o mesmo nome em dois ou mais módulos. No entanto, você deve qualificar qualquer referência a tal membro com o nome do módulo apropriado se a referência for de fora desse módulo. Para obter mais informações, consulte [referências a elementos](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)declarados.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Tipo de promoção](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
