---
title: Processando o arquivo XML (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML comments, parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
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
ms.openlocfilehash: 72b2832d0131adf39a37ebd9297b43fb34ea49ba
ms.lasthandoff: 03/13/2017

---
# <a name="processing-the-xml-file-visual-basic"></a>Processando o arquivo XML (Visual Basic)
O compilador gera uma cadeia de caracteres de identificação para cada constructo no seu código marcado para gerar a documentação. (Para obter informações sobre como marcar seu código, consulte [marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).) A cadeia de caracteres de identificação identifica exclusivamente o constructo. Programas que processam o arquivo XML podem usar a cadeia de caracteres de identificação para identificar o correspondente [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] item metadados/reflexão.  
  
 O arquivo XML não é uma representação hierárquica de seu código; é uma lista simples com uma identificação gerada para cada elemento.  
  
 O compilador observa as regras a seguir quando ele gera as cadeias de caracteres de ID:  
  
-   Nenhum espaço em branco é colocado na cadeia de caracteres.  
  
-   A primeira parte da cadeia de caracteres de identificação identifica o tipo de membro está sendo identificado, com um único caractere seguido por dois pontos. Os seguintes tipos de membro são usados.  
  
|Caractere|Descrição|  
|---|---|  
|N|namespace<br /><br /> Não é possível adicionar comentários de documentação a um namespace, mas você pode fazer referências CREF a eles, onde há suporte.|  
|T|type: `Class`, `Module`, `Interface`, `Structure`, `Enum`,`Delegate`|  
|F|campo:`Dim`|  
|P|propriedade: `Property` (incluindo propriedades padrão)|  
|M|method: `Sub`, `Function`, `Declare`,`Operator`|  
|E|evento:`Event`|  
|!|cadeia de caracteres de erro<br /><br /> O restante da cadeia de caracteres fornece informações sobre o erro. O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador gera informações de erro para links que não podem ser resolvidos.|  
  
-   A segunda parte do `String` é o nome totalmente qualificado do item, iniciando na raiz do namespace. O nome do item, seus tipos delimitador e o namespace são separados por pontos. Se o nome do próprio item contiver períodos, eles serão substituídos pelo sinal numérico (#). Supõe-se que nenhum item possui um sinal de número diretamente no seu nome. Por exemplo, o nome totalmente qualificado do `String` construtor seria `System.String.#ctor`.  
  
-   Para propriedades e métodos, se houver argumentos para o método, segue a lista de argumentos entre parênteses. Se não houver nenhum argumento, nenhum parêntese estará presente. Os argumentos são separados por vírgulas. A codificação de cada argumento segue diretamente como ela é codificada em um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assinatura.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como a ID de cadeias de caracteres para uma classe e seus membros são gerados.  
  
 [!code-vb[VbVbcnXmlDocComments n º&10;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
