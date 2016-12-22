---
title: "Instru&#231;&#227;o Imports (tipo e namespace .NET) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Imports"
  - "imports"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "aliases [Visual Basic], import"
  - "aliases [Visual Basic], Instrução Imports"
  - "elementos de contêiner [Visual Basic]"
  - "nomes de elementos declarados [Visual Basic], qualificação"
  - "elementos declarados [Visual Basic], elementos de contêiner"
  - "importar aliases [Visual Basic]"
  - "imports [Visual Basic]"
  - "instrução Imports [Visual Basic]"
  - "instrução Imports [Visual Basic], sintaxe"
  - "namespaces [Visual Basic], importando"
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
caps.latest.revision: 40
caps.handback.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Imports (tipo e namespace .NET)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Permite digitar os nomes a ser referenciado sem qualificação do espaço para nome.  
  
## Sintaxe  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`aliasname`|Opcional.  Um *pseudônimo de importação* ou nome pelo qual o código refere\-se a `namespace` ao invés da cadeia de caracteres de qualificação completa.  Veja [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Necessário.  O nome completamente qualificado do namespace sendo importado.  Pode ser uma cadeia de caracteres de namespaces aninhados em qualquer nível.|  
|`element`|Opcional.  O nome do elemento de programação declarado no namespace.  Pode ser qualquer elemento contêiner.|  
  
## Comentários  
 O `Imports`  instrução permite que os tipos contidos em um determinado namespace para ser referenciado diretamente.  
  
 Você pode fornecer um único nome de namespace ou uma cadeia de caracteres de namespaces aninhados.  Cada namespace aninhado é separado do namespace do nível imediatamente mais alto por um ponto final \(`.`\), como o exemplo a seguir ilustra.  
  
 `Imports System.Collections.Generic`  
  
 Cada arquivo\-fonte pode conter qualquer número de declarações `Imports`.  Estas deve seguir qualquer declaração de opção, como a declaração `Option Strict`, e eles devem preceder qualquer declaração de elemento de programação, como declarações `Module` ou `Class`.  
  
 Você pode usar `Imports` apenas em nível de arquivo.  Isso significa que o contexto da declaração para importação deve ser um arquivo\-fonte, e não um namespace, estrutura, módulo, interface, procedimento ou bloco.  
  
 Observe que a declaração `Imports` não cria elementos a partir de outros projetos e assemblies disponíveis para seu projeto.  Importar não toma o lugar de configurar uma referência.  Isso apenas remove a necessidade de se qualificar nome já estão disponíveis para seu projeto.  Para mais informação veja "Importing Containing Elements" in [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
>  Você pode definir implícito `Imports` instruções usando a [Página Referências, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic).  Para mais informações, consulte [Como adicionar ou remover namespaces importados \(Visual Basic\)](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20\(Visual%20Basic\).md).  
  
## Aliases de importação  
 Um  *Importar alias* define o alias para um namespace ou tipo.  Pseudônimos Import são úteis quando você necessita usar itens como o mesmo nome que está declarado em um ou mais namespaces.  Para obter mais informações e um exemplo, consulte "Qualificação de um nome de elemento" em [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Você não deve declarar um membro no nível de módulo com o mesmo nome de `aliasname`.  Se você o fizer, o compilador do Visual Basic utiliza `aliasname` apenas para o membro declarado e não o reconhece mais como um pseudônimo import.  
  
 Embora a sintaxe usada para se declarar um pseudimo Import é como aquela usada para importar um prefixo de namespace XML, os resultados são diferente.  Um pseudônimo Import pode ser usado como uma expressão no seu código, ao passo que um prefixo de namespace XML pode ser usado apenas em literais XML ou propriedades de eixo XML como o prefixo para um nome habilitado ou nome de atributo.  
  
### Nomes de elementos  
 Se você fornecer `element`, ele deve representar uma  *elemento contêiner*, ou seja, um elemento de programação que pode conter outros elementos.  Elementos contêiner incluem classes, estruturas, módulos, interfaces e enumerações.  
  
 O escopo dos elementos disponibilizados por um `Imports` instrução depende se você especificar `element`.  Se você especificar apenas `namespace`, todos os membros nomeados univocamente daquele namespace e os elementos contêiner dentro daquele namespace estão disponíveis sem habilitação.  Se você especificar ambos `namespace` e `element`, apenas os membros daquele elemento estão disponíveis sem habilitação.  
  
## Exemplo  
 O exemplo a seguir retorna todas as pastas no diretório C:\\ usando o <xref:System.IO.DirectoryInfo> classe.  
  
 O código tem não `Imports` instruções na parte superior do arquivo.  Portanto, o `DirectoryInfo`, <xref:System.Text.StringBuilder>, e <xref:Microsoft.VisualBasic.ControlChars.CrLf> as referências são inteiramente qualificadas com os espaços para nome.  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## Exemplo  
 O exemplo a seguir inclui `Imports` instruções para namespaces referenciados.  Portanto, os tipos precisam ser totalmente qualificados com os espaços para nome.  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## Exemplo  
 O exemplo a seguir inclui `Imports` instruções que criam aliases para os espaços para nome referenciados.  Os tipos são qualificados com os aliases.  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## Exemplo  
 O exemplo a seguir inclui `Imports` instruções que criam aliases para os tipos de referência.  Os aliases são usados para especificar os tipos.  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## Consulte também  
 [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Instrução Imports \(namespace XML\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)