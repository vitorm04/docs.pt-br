---
title: Instrução Imports - .NET Namespace e tipo (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
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
ms.openlocfilehash: 4574bab62ca6d095ab66c17bf186da5f3d79bfb7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826516"
---
# <a name="imports-statement-net-namespace-and-type"></a>Instrução Imports (tipo e namespace .NET)
Permite que digite o nome para ser referenciados sem qualificação de namespace.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`aliasname`|Opcional. Uma *alias de importação* ou o nome pelo qual o código pode se referir a `namespace` em vez da cadeia de caracteres de qualificação completa. Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Necessário. O nome totalmente qualificado do namespace que está sendo importado. Pode ser uma cadeia de caracteres de namespaces aninhada em qualquer nível.|  
|`element`|Opcional. O nome de um elemento de programação declarado no namespace. Pode ser qualquer elemento de contêiner.|  
  
## <a name="remarks"></a>Comentários  
 O `Imports` instrução permite tipos que estão contidos em um namespace específico a ser referenciado diretamente.  
  
 Você pode fornecer um nome de namespace único ou uma cadeia de caracteres de namespaces aninhados. Cada namespace aninhado é separado do namespace de nível superior próximo por um período (`.`), como mostra o exemplo a seguir.  
  
 `Imports System.Collections.Generic`  
  
 Cada arquivo de origem pode conter qualquer número de `Imports` instruções. Estas deve seguir qualquer declaração de opção, como o `Option Strict` instrução e eles devem preceder qualquer declaração de elemento de programação, como `Module` ou `Class` instruções.  
  
 Você pode usar `Imports` apenas no nível de arquivo. Isso significa que o contexto da declaração de importação deve ser um arquivo de origem e não pode ser um namespace, classe, estrutura, módulo, interface, procedimento ou bloco.  
  
 Observe que o `Imports` instrução não torna os elementos de outros projetos e assemblies disponíveis para seu projeto. Importar não toma o lugar de uma referência de configuração. Ele apenas remove a necessidade de qualificar nomes que já estão disponíveis para seu projeto. Para obter mais informações, consulte "Importação de elementos que contém" na [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
>  Você pode definir implícita `Imports` instruções usando o [página referências, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic). Para obter mais informações, confira [Como: Adicionar ou remover Namespaces importados (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
## <a name="import-aliases"></a>Aliases de importação  
 Uma *importação alias* define o alias para um namespace ou tipo. Aliases de importação são úteis quando você precisa usar itens com o mesmo nome que são declarados em um ou mais namespaces. Para obter mais informações e um exemplo, consulte "Qualificando um nome de elemento" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Você não deve declarar um membro no nível de módulo com o mesmo nome que `aliasname`. Se você fizer isso, o compilador do Visual Basic usa `aliasname` somente para o membro declarado e não está mais reconhece como um alias de importação.  
  
 Embora a sintaxe usada para declarar um alias de importação é como aquela usada para importar um prefixo de namespace XML, os resultados são diferentes. Um alias de importação pode ser usado como uma expressão em seu código, enquanto que um prefixo de namespace XML pode ser usado apenas em literais XML ou propriedades de eixo XML como o prefixo para um elemento qualificado ou o nome do atributo.  
  
### <a name="element-names"></a>Nomes de elementos  
 Se você fornecer `element`, ele deve representar uma *elemento contêiner*, ou seja, um elemento de programação que pode conter outros elementos. Elementos de contêiner incluem classes, estruturas, módulos, interfaces e enumerações.  
  
 O escopo dos elementos disponibilizado por um `Imports` instrução depende se você especificar `element`. Se você especificar apenas `namespace`, tudo exclusivamente nomeada membros desse namespace e os elementos de contêiner dentro desse namespace, estão disponíveis sem qualificação. Se você especificar ambos `namespace` e `element`, somente os membros desse elemento estão disponíveis sem qualificação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna todas as pastas no diretório c:\. usando o <xref:System.IO.DirectoryInfo> classe.  
  
 O código não tem nenhum `Imports` instruções na parte superior do arquivo. Portanto, o `DirectoryInfo`, <xref:System.Text.StringBuilder>, e <xref:Microsoft.VisualBasic.ControlChars.CrLf> referências são todas totalmente qualificadas com os namespaces.  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inclui `Imports` instruções para os namespaces referenciados. Portanto, os tipos não precisam ser totalmente qualificados com os namespaces.  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inclui `Imports` instruções que criam aliases para os namespaces referenciados. Os tipos são qualificados com os aliases.  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inclui `Imports` instruções que criam aliases para tipos referenciados. Os aliases são usados para especificar os tipos.  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Referências e a Instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Instrução Imports (Namespace de XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
