---
title: /doc
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1f9d4f584f217e6996a499614b97f184b28664f8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
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
|`+` &#124; `-`|Opcional. Especificar +, ou apenas `/doc`, faz com que o compilador gere informações sobre a documentação e colocá-lo em um arquivo XML. Especificando `-` é o equivalente de não especificar `/doc`, fazendo com que nenhuma informação documentação a ser criado.|  
|`file`|Necessário se `/doc:` for usado. Especifica o arquivo XML de saída, que é preenchido com os comentários dos arquivos de código-fonte da compilação. Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").|  
  
## <a name="remarks"></a>Comentários  
 O `/doc` opção controla se o compilador gera um arquivo XML que contém os comentários de documentação. Se você usar o `/doc:``file` sintaxe, o `file` parâmetro especifica o nome do arquivo XML. Se você usar `/doc` ou `/doc+`, o compilador usa o nome do arquivo XML do arquivo executável ou biblioteca que está sendo criada pelo compilador. Se você usar `/doc-` ou não especifique o `/doc` opção, o compilador não cria um arquivo XML.  
  
 Nos arquivos de código-fonte, comentários de documentação podem preceder as seguintes definições:  
  
-   Definido pelo usuário tipos, como um [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou [interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Membros, como um campo, [evento](../../../visual-basic/language-reference/statements/event-statement.md), [propriedade](../../../visual-basic/language-reference/statements/property-statement.md), [função](../../../visual-basic/language-reference/statements/function-statement.md), ou [sub-rotina](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Para usar o arquivo XML gerado com o [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) recurso, deixe o nome do arquivo do arquivo XML ser o mesmo que o assembly que você deseja dar suporte. Verifique se o arquivo XML está no mesmo diretório que o assembly para que quando o assembly é referenciado no [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] projeto, o arquivo. XML seja encontrado também. Arquivos de documentação XML não são necessários para IntelliSense para funcionar com o código dentro de um projeto ou em projetos referenciados por um projeto.  
  
 A menos que você compile com `/target:module`, o arquivo XML contém as marcas `<assembly></assembly>`. Essas marcas especificam o nome do arquivo que contém o manifesto do assembly para o arquivo de saída da compilação.  
  
 Consulte [marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) maneiras de gerar documentação de comentários em seu código.  
  
|Configurar /doc no Visual Studio ambiente de desenvolvimento integrado|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Definir o valor no **arquivo de documentação XML gerar** caixa.|  
  
## <a name="example"></a>Exemplo  
 Consulte [documentar seu código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) para obter um exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Documentando o Código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
