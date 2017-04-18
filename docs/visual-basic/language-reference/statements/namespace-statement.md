---
title: "Instrução Namespace | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Namespace
dev_langs:
- VB
helpviewer_keywords:
- namespaces, root
- Namespace statement
- namespaces, nested
- declaring namespaces, syntax
- namespaces, declaring
- root namespaces
- declarations, namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
caps.latest.revision: 39
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 525259345bbfa5ba0e197a4dffbed469077700cf
ms.lasthandoff: 03/13/2017

---
# <a name="namespace-statement"></a>Instrução Namespace
Declara o nome de um namespace e faz com que o código-fonte que segue a declaração seja compilado dentro desse namespace.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Partes  
 Global  
 Opcional. Permite definir um namespace fora do namespace raiz do projeto. Consulte [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Necessário. Um nome exclusivo que identifica o namespace. Deve ser um identificador válido Visual Basic. Para obter mais informações, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 Opcional. Elementos que compõem o namespace. Esses incluem, mas não estão limitadas a, enumerações, estruturas, interfaces, classes, módulos, representantes e outros namespaces.  
  
 `End Namespace`  
 Finaliza uma `Namespace` bloco.  
  
## <a name="remarks"></a>Comentários  
 Namespaces são usados como um sistema organizacional. Eles fornecem uma maneira de classificar e apresentar os elementos de programação que são expostos a outros programas e aplicativos. Observe que um namespace não é um *tipo* no sentido de que uma classe ou estrutura é — você não pode declarar um elemento de programação para ter o tipo de dados de um namespace.  
  
 Todos os elementos de programação declarados após uma `Namespace` instrução pertencem a esse namespace. Visual Basic continua a compilar elementos no último namespace declarado até encontrar uma `End Namespace` instrução ou outro `Namespace` instrução.  
  
 Se um namespace já estiver definido, até mesmo fora do seu projeto, você pode adicionar elementos de programação a ele. Para fazer isso, você deve usar um `Namespace` instrução para direcionar o Visual Basic para compilar os elementos para esse namespace.  
  
 Você pode usar um `Namespace` instrução somente no nível de namespace ou arquivo. Isso significa que o *contexto declaração* para um namespace deve ser um arquivo fonte ou namespace e não pode ser uma classe, estrutura, módulo, interface ou procedimento. Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Você pode declarar um namespace dentro de outro. Não há nenhum limite estrito aos níveis de aninhamento você pode declarar, mas lembre-se de que, quando outro código acessa os elementos declarados no namespace mais interno, ele deve usar uma cadeia de caracteres de qualificação que contém todos os nomes de namespaces na hierarquia de aninhamento.  
  
## <a name="access-level"></a>Nível de acesso  
 Namespaces são tratados como se tivessem um `Public` nível de acesso. Um namespace pode ser acessado de código em qualquer lugar no mesmo projeto, de outros projetos que referenciem o projeto e de qualquer assembly compilado do projeto.  
  
 Elementos de programação declarados no nível de namespace, que significa que em um namespace mas não dentro de qualquer outro elemento, podem ter `Public` ou `Friend` acesso. Se não for especificado, o nível de acesso de tal elemento usa `Friend` por padrão. Você pode declarar no nível de namespace de elementos incluem classes, estruturas, módulos, interfaces, enumerações e delegados. Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Namespace Raiz  
 Todos os nomes de namespace em seu projeto são baseados em um *namespace raiz*. Visual Studio atribui o nome do projeto como o namespace de raiz padrão para todo o código em seu projeto. Por exemplo, se seu projeto for chamado `Payroll`, seus elementos de programação pertencem ao namespace `Payroll`. Se você declarar `Namespace funding`, é o nome completo do namespace `Payroll.funding`.  
  
 Se você quiser especificar um namespace existente em um `Namespace` instrução, como no exemplo de classe de lista genérica, você pode definir seu namespace raiz com um valor nulo. Para fazer isso, clique em **propriedades do projeto** do **projeto** menu e desmarque o **namespace raiz** entrada para que a caixa estiver vazia. Se você não fizer isso no exemplo de classe de lista genérica, o compilador Visual Basic tomaria `System.Collections.Generic` como um novo namespace no projeto `Payroll`, com o nome completo do `Payroll.System.Collections.Generic`.  
  
 Como alternativa, você pode usar o `Global` palavra-chave para se referir a elementos de namespaces definidos fora do projeto. Isso permite que você mantenha o nome do projeto como o namespace raiz. Isso reduz a chance de mesclagem, inadvertidamente, elementos de programação com os dos namespaces existentes. Para obter mais informações, consulte a seção "Global palavra-chave em nomes totalmente qualificados" [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 O `Global` palavra-chave também pode ser usado em uma declaração de Namespace. Isso permite definir um namespace fora do namespace raiz do projeto. Para obter mais informações, consulte a seção "Palavra-chave no Namespace instruções globais" [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Solução de problemas.** O namespace raiz pode levar à concatenações inesperadas de nomes de namespace. Se você fizer referência a namespaces definidos fora do projeto, o compilador do Visual Basic pode construe-los como namespaces aninhados no namespace raiz. Nesse caso, o compilador não reconhece quaisquer tipos que tiverem sido já definidos em namespaces externos. Para evitar isso, defina seu namespace raiz com um valor nulo, conforme descrito em "Namespace raiz", ou use o `Global` palavra-chave para acessar elementos de namespaces externos.  
  
## <a name="attributes-and-modifiers"></a>Atributos e modificadores  
 Você não pode aplicar atributos a um namespace. Um atributo contribui com informações para metadados do assembly, que não é significativo para fontes classificadores como namespaces.  
  
 É possível aplicar qualquer acesso ou modificadores de procedimento ou qualquer outros modificadores, a um namespace. Porque ele não é um tipo, esses modificadores não são significativos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara dois namespaces, um aninhado no outro.  
  
 [!code-vb[VbVbalrStatements&#43;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara vários namespaces aninhados em uma única linha, e é equivalente ao exemplo anterior.  
  
 [!code-vb[41 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir acessa a classe definida nos exemplos anteriores.  
  
 [!code-vb[VbVbalrStatements&42;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define o esqueleto de uma nova classe de lista genérica e adiciona-o para o <xref:System.Collections.Generic?displayProperty=fullName>namespace.</xref:System.Collections.Generic?displayProperty=fullName>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
