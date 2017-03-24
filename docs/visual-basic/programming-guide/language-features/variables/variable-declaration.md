---
title: "Declaração de variável no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables, declarations
- Dim statement, variable declaration
- declaring variables
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime, variables
- variables [Visual Basic], lifetime
- access levels, variables
- scope, declaration statements
- variables [Visual Basic], access level
- local variables, declarations
- scope, variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8cabb2d319288653c80099c816e46e822429d6ec
ms.lasthandoff: 03/13/2017

---
# <a name="variable-declaration-in-visual-basic"></a>Declaração de variável no Visual Basic
Você declara uma variável para especificar seu nome e suas características. A instrução de declaração para variáveis é a [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Sua localização e conteúdo determinam as características da variável.  
  
 Para regras de nomenclatura de variáveis e considerações, consulte [nomes de elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Níveis de declaração  
  
### <a name="local-and-member-variables"></a>Local e variáveis de membro  
 A *variável local* é aquela declarada dentro de um procedimento. A *variável de membro* é um membro de um [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] digite; ela é declarada no nível de módulo, dentro de uma classe, estrutura ou módulo, mas não dentro de qualquer procedimento interno para essa classe, estrutura ou módulo.  
  
### <a name="shared-and-instance-variables"></a>Compartilhado e variáveis de instância  
 Em uma classe ou estrutura, a categoria de uma variável de membro depende se ela é compartilhada. Se ela for declarada com a [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) , é um *variável compartilhada*, e existe em uma única cópia compartilhada entre todas as instâncias da classe ou estrutura.  
  
 Caso contrário, será uma *variável de instância*, e uma cópia separada é criada para cada instância da classe ou estrutura. Uma cópia determinada de uma variável de instância está disponível somente para a instância da classe ou estrutura na qual ele foi criado. Isso é independente de uma cópia da variável de instância em qualquer outra instância da classe ou estrutura.  
  
## <a name="declaring-data-type"></a>Declarar o tipo de dados  
 O [como](../../../../visual-basic/language-reference/statements/as-clause.md) cláusula na instrução de declaração permite que você defina o tipo de dados ou tipo de objeto da variável que é declarado. Você pode especificar qualquer um dos seguintes tipos para uma variável:  
  
-   Digite um dados elementar, como `Boolean`, `Long`, ou`Decimal`  
  
-   Um tipo de dados compostos, como uma matriz ou estrutura  
  
-   Um tipo de objeto ou classe, definida em seu aplicativo ou em outro aplicativo  
  
-   A [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] classe, como <xref:System.Windows.Forms.Label>ou <xref:System.Windows.Forms.TextBox></xref:System.Windows.Forms.TextBox> </xref:System.Windows.Forms.Label>  
  
-   Tipo de uma interface, como <xref:System.IComparable>ou <xref:System.IDisposable></xref:System.IDisposable> </xref:System.IComparable>  
  
 Você pode declarar diversas variáveis em uma instrução sem a necessidade de repetir o tipo de dados. Nas instruções a seguir, as variáveis `i`, `j`, e `k` são declaradas como tipo `Integer`, `l` e `m` como `Long`, e `x` e `y` como `Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Para obter mais informações sobre tipos de dados, consulte [tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md). Para obter mais informações sobre objetos, consulte [objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) e [Programando com componentes](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
## <a name="local-type-inference"></a>Inferência de tipo local  
 *Inferência de tipo* é usado para determinar os tipos de dados de variáveis locais declarados sem um `As` cláusula. O compilador infere o tipo da variável do tipo da expressão de inicialização. Isso permite que você declarar variáveis sem indicar um tipo explicitamente. No exemplo a seguir, ambos `num1` e `num2` são fortemente tipadas como inteiros.  
  
 [!code-vb[VbVbalrTypeInference n º&1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 Se você quiser usar inferência de tipo local, `Option Infer` deve ser definido como `On`. Para obter mais informações, consulte [inferência de tipo Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) e [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Características de variáveis declaradas  
 O *tempo de vida* de uma variável é o período de tempo durante o qual ele está disponível para uso. Em geral, existe uma variável como o elemento que declara (por exemplo, um procedimento ou classe) continua a existir. Se a variável não precisa continuar existindo além do tempo de vida do elemento que a contém, você não precisa fazer nada especial na declaração. Se a variável precisa continuar existindo mais que o elemento que contém, você pode incluir o `Static` ou `Shared` palavra-chave em seu `Dim` instrução. Para obter mais informações, consulte [tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 O *escopo* de uma variável é o conjunto de todo o código que pode fazer referência a ele sem qualificar seu nome. Escopo de uma variável é determinado por onde ela é declarada. Código localizado em uma região determinada pode usar as variáveis definidas naquela região sem ter que qualificar seus nomes. Para obter mais informações, consulte [escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 Uma variável *nível de acesso* é a extensão de código que tenha permissão para acessá-lo. Isso é determinado pelo modificador de acesso (como [pública](../../../../visual-basic/language-reference/modifiers/public.md) ou [particular](../../../../visual-basic/language-reference/modifiers/private.md)) que você usar o `Dim` instrução. Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar uma nova variável](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)   
 [Como: mover dados dentro e fora de uma variável](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [Estático](../../../../visual-basic/language-reference/modifiers/static.md)   
 [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
