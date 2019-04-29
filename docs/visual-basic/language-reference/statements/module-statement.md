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
ms.openlocfilehash: f546498e5282bcf58d07a06968bb4303e4e6d7b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784157"
---
# <a name="module-statement"></a>Instrução Module
Declara o nome de um módulo e introduz a definição de variáveis, propriedades, eventos e procedimentos que compõem o módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a>Partes  
 `attributelist`  
 Opcional. Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Opcional. Pode ser uma das seguintes opções:  
  
- [Público](../../../visual-basic/language-reference/modifiers/public.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 Ver [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `name`  
 Necessário. Nome do módulo. Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `statements`  
 Opcional. Instruções que definem variáveis, propriedades, eventos, procedimentos e tipos aninhados deste módulo.  
  
 `End Module`  
 Encerra o `Module` definição.  
  
## <a name="remarks"></a>Comentários  
 Um `Module` instrução define um tipo de referência disponível em todo o namespace. Um *módulo* (às vezes chamado de um *módulo padrão*) é semelhante a uma classe, mas com algumas diferenças importantes. Cada módulo tem exatamente uma instância e não precisa ser criado ou atribuído a uma variável. Módulos não dão suporte à herança ou implementar interfaces. Observe que um módulo não é um *tipo* no sentido de que uma classe ou estrutura é — você não pode declarar um elemento de programação para ter o tipo de dados de um módulo.  
  
 Você pode usar `Module` somente no nível de namespace. Isso significa que o *contexto de declaração* para um módulo deve ser um arquivo de origem ou namespace e não pode ser uma classe, estrutura, módulo, interface, procedimento ou bloco. Não é possível aninhar um módulo dentro de outro módulo, ou em qualquer tipo. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Um módulo tem a mesma duração do seu programa. Como seus membros são todos os `Shared`, eles também têm vida útil igual a do programa.  
  
 Módulos padrão [amigo](../../../visual-basic/language-reference/modifiers/friend.md) acesso. Você pode ajustar os níveis de acesso com os modificadores de acesso. Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Todos os membros de um módulo são implicitamente `Shared`.  
  
## <a name="classes-and-modules"></a>Classes e módulos  
 Esses elementos têm muitas semelhanças, mas há algumas diferenças importantes também.  
  
- **Terminologia.** As versões anteriores do Visual Basic reconhecem os dois tipos de módulos: *módulos de classe* (CLS arquivos) e *módulos padrão* (arquivos. bas). A versão atual chama esses *classes* e *módulos*, respectivamente.  
  
- **Membros compartilhados.** Você pode controlar se um membro de uma classe pode ser compartilhado ou membro de instância.  
  
- **Orientação a objeto.** As classes são orientada a objeto, mas os módulos não são. Classes só podem ser instanciadas como objetos. Para obter mais informações, consulte [objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="rules"></a>Regras  
  
- **Modificadores.** Todos os membros do módulo são implicitamente [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md). Não é possível usar o `Shared` palavra-chave quando declarar um membro e você não pode alterar o status compartilhado de nenhum membro.  
  
- **Herança.** Um módulo não pode herdar de qualquer tipo diferente de <xref:System.Object>, da quais todos os módulos são herdadas. Em particular, um módulo não pode herdar de outra.  
  
     Não é possível usar o [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) em uma definição de módulo, mesmo para especificar <xref:System.Object>.  
  
- **Propriedade padrão.** Você não pode definir as propriedades padrão em um módulo. Para obter mais informações, consulte [padrão](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Comportamento  
  
- **Nível de acesso.** Dentro de um módulo, você pode declarar cada membro com seu próprio nível de acesso. Membros de módulo padrão [pública](../../../visual-basic/language-reference/modifiers/public.md) acessar, exceto as variáveis e constantes, que usam como padrão [privada](../../../visual-basic/language-reference/modifiers/private.md) acesso. Quando um módulo tem mais acesso restrito que um de seus membros, o nível de acesso do módulo especificado terá precedência.  
  
- **Escopo.** Um módulo está no escopo em todo o namespace.  
  
     O escopo de cada membro de módulo é todo o módulo. Observe que todos os membros sofrem *promoção de tipos*, que faz com que o escopo ser promovido para o namespace que contém o módulo. Para obter mais informações, consulte [promoção de tipo](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
- **Qualificação.** Você pode ter vários módulos em um projeto, e você pode declarar membros com o mesmo nome em duas ou mais módulos. No entanto, você deve qualificar qualquer referência a esse membro com o nome do módulo apropriado se a referência estiver fora desse módulo. Para obter mais informações, consulte [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Tipo de promoção](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
