---
title: /doc | Documentos do Microsoft
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
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: 18
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
ms.openlocfilehash: 1054eb256eb7670ee0454b02fc094e0306c1218d
ms.lasthandoff: 03/13/2017

---
# <a name="doc"></a>/doc
Processa comentários de documentação para um arquivo XML.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. Especificar +, ou apenas `/doc`, faz com que o compilador gere informações sobre a documentação e colocá-lo em um arquivo XML. Especificando `-` é o equivalente de não especificar `/doc`, fazendo com que nenhuma informação documentação seja criada.|  
|`file`|Necessário se `/doc:` for usado. Especifica o arquivo XML de saída, que é preenchido com os comentários dos arquivos de código-fonte da compilação. Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").|  
  
## <a name="remarks"></a>Comentários  
 O `/doc` opção controla se o compilador gera um arquivo XML contendo comentários de documentação. Se você usar o `/doc:``file` sintaxe, o `file` parâmetro especifica o nome do arquivo XML. Se você usar `/doc` ou `/doc+`, o compilador pega o nome do arquivo XML do arquivo executável ou biblioteca que está sendo criada pelo compilador. Se você usar `/doc-` ou não especifique o `/doc` opção, o compilador não cria um arquivo XML.  
  
 Em arquivos de código-fonte, comentários documentação podem preceder as seguintes definições:  
  
-   Definido pelo usuário tipos, como um [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou [interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Membros, como um campo, [evento](../../../visual-basic/language-reference/statements/event-statement.md), [propriedade](../../../visual-basic/language-reference/statements/property-statement.md), [função](../../../visual-basic/language-reference/statements/function-statement.md), ou [sub-rotina](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Para usar o arquivo XML gerado com o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] [IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense) recurso, deixe o nome do arquivo do arquivo XML ser o mesmo que o assembly que você deseja oferecer suporte. Verifique se o arquivo XML está no mesmo diretório que o assembly para que quando o assembly for referenciado no [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] projeto, o arquivo. XML seja encontrado também. Arquivos de documentação XML não são necessários para IntelliSense para funcionar com código em um projeto ou em projetos referenciados por um projeto.  
  
 A menos que você compile com `/target:module`, o arquivo XML contém as marcas `<assembly></assembly>`. Essas marcas especificam o nome do arquivo que contém o manifesto do assembly para o arquivo de saída da compilação.  
  
 Consulte [marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) de maneiras de gerar documentação de comentários em seu código.  
  
|Configurar /doc no Visual Studio ambiente de desenvolvimento integrado|  
|---|  
|1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na guia **Compilar**.<br />3.  Defina o valor no **arquivo de documentação XML gerar** caixa.|  
  
## <a name="example"></a>Exemplo  
 Consulte [documentar seu código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) para obter um exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Documentando o Código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
