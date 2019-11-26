---
title: Processando o arquivo XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 4230fd88b4b60c631135f5b7fb15f4b6272b5351
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347297"
---
# <a name="processing-the-xml-file-visual-basic"></a>Processando o arquivo XML (Visual Basic)
O compilador gera uma cadeia de identificação para cada constructo no seu código marcado para gerar a documentação. (For information on how to tag your code, see [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct. Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.  
  
 The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.  
  
 O compilador observa as seguintes regras quando gera as cadeias de identificação:  
  
- Nenhum espaço em branco é colocado na cadeia de caracteres.  
  
- A primeira parte da cadeia de identificação identifica o tipo de membro que está sendo identificado, com um único caractere seguido por dois-pontos. The following member types are used.  
  
|Caractere|Descrição|  
|---|---|  
|N|namespace<br /><br /> You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.|  
|T|type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|field: `Dim`|  
|P|property: `Property` (including default properties)|  
|M|method: `Sub`, `Function`, `Declare`, `Operator`|  
|E|event: `Event`|  
|!|cadeia de caracteres de erro<br /><br /> O restante da cadeia de caracteres fornece informações sobre o erro. The Visual Basic compiler generates error information for links that cannot be resolved.|  
  
- The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace. The name of the item, its enclosing type(s), and the namespace are separated by periods. If the name of the item itself contains periods, they are replaced by the number sign (#). It is assumed that no item has a number sign directly in its name. For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.  
  
- Para propriedades e métodos, se houver argumentos para o método, seguirá a lista de argumentos entre parênteses. Se não houver nenhum argumento, não haverá parênteses. Os argumentos são separados por vírgulas. The encoding of each argument follows directly how it is encoded in a .NET Framework signature.  
  
## <a name="example"></a>Exemplo  
 The following code shows how the ID strings for a class and its members are generated.  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Consulte também

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
