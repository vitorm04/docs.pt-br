---
title: Processando o arquivo XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 91583612940282b05ebbf38bd5f0a59d6af5bbcd
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524453"
---
# <a name="processing-the-xml-file-visual-basic"></a>Processando o arquivo XML (Visual Basic)
O compilador gera uma cadeia de identificação para cada constructo no seu código marcado para gerar a documentação. (Para obter informações sobre como marcar seu código, consulte [marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/index.md).) A cadeia de caracteres de ID identifica exclusivamente a construção. Programas que processam o arquivo XML podem usar a cadeia de caracteres de ID para identificar o item de metadados/reflexão .NET Framework correspondente.  
  
 O arquivo XML não é uma representação hierárquica do seu código; é uma lista simples com uma ID gerada para cada elemento.  
  
 O compilador observa as seguintes regras quando gera as cadeias de identificação:  
  
- Nenhum espaço em branco é colocado na cadeia de caracteres.  
  
- A primeira parte da cadeia de identificação identifica o tipo de membro que está sendo identificado, com um único caractere seguido por dois-pontos. Os seguintes tipos de membro são usados.  
  
|Caractere|Descrição|  
|---|---|  
|N|namespace<br /><br /> Você não pode adicionar comentários de documentação a um namespace, mas pode fazer referências CREF a eles, quando houver suporte.|  
|T|tipo: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|campo: `Dim`|  
|P|Propriedade: `Property` (incluindo as propriedades padrão)|  
|M|método: `Sub`, `Function`, `Declare` `Operator`|  
|E|evento: `Event`|  
|!|cadeia de caracteres de erro<br /><br /> O restante da cadeia de caracteres fornece informações sobre o erro. O compilador Visual Basic gera informações de erro para links que não podem ser resolvidos.|  
  
- A segunda parte da `String` é o nome totalmente qualificado do item, começando na raiz do namespace. O nome do item, seus tipos de delimitador e o namespace são separados por pontos. Se o nome do próprio item contiver pontos, eles serão substituídos pelo sinal numérico (#). Supõe-se que nenhum item tenha um sinal de número diretamente em seu nome. Por exemplo, o nome totalmente qualificado do construtor de `String` seria `System.String.#ctor`.  
  
- Para propriedades e métodos, se houver argumentos para o método, seguirá a lista de argumentos entre parênteses. Se não houver nenhum argumento, não haverá parênteses. Os argumentos são separados por vírgulas. A codificação de cada argumento segue diretamente como ele é codificado em uma assinatura .NET Framework.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como as cadeias de caracteres de ID para uma classe e seus membros são gerados.  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Consulte também

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
