---
title: "Instrução Imports (tipo e Namespace .NET) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Imports
- imports
dev_langs:
- VB
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
caps.latest.revision: 40
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
ms.openlocfilehash: 393f3e9a264817d8658585267c954d973290530a
ms.lasthandoff: 03/13/2017

---
# <a name="imports-statement-net-namespace-and-type"></a>Instrução Imports (tipo e namespace .NET)
Permite digitar os nomes para se referir a qualificação de namespace.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`aliasname`|Opcional. Um *alias de importação* ou nome pelo qual o código pode se referir a `namespace` em vez da cadeia de caracteres de qualificação completa. Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Necessário. O nome totalmente qualificado do namespace sendo importado. Pode ser uma cadeia de caracteres de namespaces aninhada em qualquer nível.|  
|`element`|Opcional. O nome de um elemento de programação declarado no namespace. Pode ser qualquer elemento contêiner.|  
  
## <a name="remarks"></a>Comentários  
 O `Imports` instrução permite tipos que estão contidos em um determinado namespace a ser referenciado diretamente.  
  
 Você pode fornecer um único nome de namespace ou uma cadeia de caracteres de namespaces aninhados. Cada namespace aninhado é separado do namespace de nível superior próximo por um período (`.`), como mostra o exemplo a seguir.  
  
 `Imports System.Collections.Generic`  
  
 Cada arquivo de origem pode conter qualquer número de `Imports` instruções. Estas deve seguir qualquer declaração de opção, como o `Option Strict` instrução e eles devem preceder qualquer declaração de elemento de programação, como `Module` ou `Class` instruções.  
  
 Você pode usar `Imports` somente no nível de arquivo. Isso significa que o contexto da declaração para importação deve ser um arquivo de origem e não pode ser um namespace, classe, estrutura, módulo, interface, procedimento ou bloco.  
  
 Observe que o `Imports` instrução não torna os elementos de outros projetos e assemblies disponíveis para seu projeto. Importar não toma o lugar de configurar uma referência. Ele apenas remove a necessidade de qualificar nomes que já estão disponíveis para seu projeto. Para obter mais informações, consulte "Importing Containing Elements" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
>  Você pode definir implícita `Imports` instruções usando o [referências de página, Designer de projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic). Para obter mais informações, consulte [como: Adicionar ou remover Namespaces importados (Visual Basic)](http://msdn.microsoft.com/library/44cebec3-0ea0-47c2-8406-4edeab6a997e).  
  
## <a name="import-aliases"></a>Aliases de importação  
 Um *alias de importação* define o alias para um namespace ou tipo. Aliases de importação são úteis quando você precisa usar itens com o mesmo nome declarado em um ou mais namespaces. Para obter mais informações e um exemplo, consulte "Qualificar um nome de elemento" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Você não deve declarar um membro no nível de módulo com o mesmo nome como `aliasname`. Se você fizer isso, o compilador do Visual Basic usa `aliasname` apenas para o membro declarado e não o reconhece como um alias de importação.  
  
 Embora a sintaxe usada para declarar um alias de importação é como aquela usada para importar um prefixo de namespace XML, os resultados são diferentes. Um alias de importação pode ser usado como uma expressão em seu código, enquanto que um prefixo de namespace XML pode ser usado apenas em literais XML ou propriedades de eixo XML como o prefixo para um elemento qualificado ou o nome do atributo.  
  
### <a name="element-names"></a>Nomes de elementos  
 Se você fornecer `element`, ele deve representar um *elemento contêiner*, ou seja, um elemento de programação que pode conter outros elementos. Elementos de contêiner incluem classes, estruturas, módulos, interfaces e enumerações.  
  
 O escopo dos elementos feitos disponíveis por uma `Imports` instrução depende de você especifica `element`. Se você especificar apenas `namespace`, tudo exclusivamente nomeado membros do namespace e os elementos de contêiner dentro desse namespace, estão disponíveis sem qualificação. Se você especificar ambas `namespace` e `element`, somente os membros daquele elemento estão disponíveis sem qualificação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna todas as pastas na pasta C:\ usando a <xref:System.IO.DirectoryInfo>classe.</xref:System.IO.DirectoryInfo>  
  
 O código não tem nenhum `Imports` instruções na parte superior do arquivo. Portanto, o `DirectoryInfo`, <xref:System.Text.StringBuilder>, e <xref:Microsoft.VisualBasic.ControlChars.CrLf>referências são inteiramente qualificadas com os namespaces.</xref:Microsoft.VisualBasic.ControlChars.CrLf> </xref:System.Text.StringBuilder>  
  
 [!code-vb[VbVbalrStatements&#152;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inclui `Imports` instruções para os namespaces referenciados. Portanto, os tipos não precisam ser totalmente qualificados com os namespaces.  
  
 [!code-vb[VbVbalrStatements&#153;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements&#154;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inclui `Imports` instruções que crie aliases para os espaços para nome referenciados. Os tipos são qualificados com os alias.  
  
 [!code-vb[VbVbalrStatements&#155;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements&#156;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inclui `Imports` instruções que criam aliases para os tipos de referência. Os aliases são usados para especificar os tipos.  
  
 [!code-vb[VbVbalrStatements&#157;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements&#158;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
