---
title: "Processando o arquivo XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comentários XML, analisando [Visual Basic]"
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Processando o arquivo XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O compilador gera uma sequência de identificação para cada constructo no seu código que está marcado para gerar a documentação.  \(Para obter informações sobre como marcar seu código, consulte [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md).\) A sequência de caracteres ID identifica exclusivamente o constructo.  Programas que processam o arquivo XML podem usar a sequência de identificação para identificar o item metadados\/reflexão[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] correspondente.  
  
 O arquivo XML é não uma representação hierárquica de seu código; é uma lista simples com uma identificação gerada para cada elemento.  
  
 O compilador observa as regras a seguir quando ele gera as sequências de identificação:  
  
-   Nenhum espaço em branco é colocado na sequência de caracteres.  
  
-   A primeira parte da sequência de identificação identifica o tipo de participante que está sendo identificada, com um único caractere seguido por dois pontos.  Os seguintes tipos membro são usados.  
  
|||  
|-|-|  
|Caracterer|Descrição|  
|N|namespace<br /><br /> Não é possível adicionar comentários de documentação a um espaço de nomes, mas você pode fazer referências CREF a eles, onde for suportado.|  
|T|Tipo: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|campo: `Dim`|  
|P|Propriedade: `Property` \(incluindo propriedades padrão\)|  
|M|método: `Sub`,`Function`,`Declare`,`Operator`|  
|E|evento: `Event`|  
|\!|sequência de caracteres de erro<br /><br /> O restante da sequência de caracteres fornece informações sobre o erro.  O compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gera informações de erro para links que não podem ser resolvidos.|  
  
-   A segunda parte da `String` é o nome totalmente qualificado do item, começando a raiz do namespace.  O nome do item, seus tipos delimitador\(es\) e o espaço de nomes são separados por pontos.  Se o próprio nome do item contiver períodos, elas serão substituídos pelo sinal de número \(\#\).  Pressupõe\-se que nenhum item possui um sinal de número diretamente no seu nome.  Por exemplo, o nome totalmente qualificado do construtor `String` seria `System.String.#ctor`.  
  
-   Para propriedades e métodos, se houver argumentos para o método, a lista de argumentos colocados entre parênteses segue.  Se não houver nenhum argumento, nenhum parêntese estará presente  Os argumentos são separados por vírgulas.  A codificação de cada argumento segue diretamente como ela é codificada em uma assinatura [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] .  
  
## Exemplo  
 O código a seguir mostra como a identificação sequências de caracteres de uma classe e seus membros são gerados.  
  
 [!code-vb[VbVbcnXmlDocComments#10](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/processing-the-xml-file_1.vb)]  
  
## Consulte também  
 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [Como criar documentação XML](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)