---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c77d063d64354bf4693ce82509f36be9d2e5b0c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44035951"
---
# <a name="-doc"></a>-doc
Processa comentários de documentação para um arquivo XML.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. Especificando +, ou apenas `-doc`, faz com que o compilador gerar informações sobre a documentação e colocá-lo em um arquivo XML. Especificando `-` é o equivalente de não especificar `-doc`, fazendo com que nenhuma informação de documentação a ser criado.|  
|`file`|Necessário se `-doc:` for usado. Especifica o arquivo XML de saída, que é populado com os comentários dos arquivos de código-fonte da compilação. Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").|  
  
## <a name="remarks"></a>Comentários  
 O `-doc` opção controla se o compilador gera um arquivo XML contendo os comentários de documentação. Se você usar o `-doc:file` sintaxe, o `file` parâmetro especifica o nome do arquivo XML. Se você usar `-doc` ou `-doc+`, o compilador pega o nome do arquivo XML do arquivo executável ou biblioteca que o compilador está criando. Se você usar `-doc-` ou não especifique o `-doc` opção, o compilador não cria um arquivo XML.  
  
 Nos arquivos de código-fonte, comentários de documentação podem preceder as seguintes definições:  
  
-   Definido pelo usuário tipos, como um [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou [interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   Membros, como um campo [evento](../../../visual-basic/language-reference/statements/event-statement.md), [propriedade](../../../visual-basic/language-reference/statements/property-statement.md), [função](../../../visual-basic/language-reference/statements/function-statement.md), ou [sub-rotina](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
 Para usar o arquivo XML gerado com o Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) recurso, deixe o nome do arquivo XML a ser o mesmo que o assembly que você deseja dar suporte. Verifique se que o arquivo XML está no mesmo diretório que o assembly para que quando o assembly for referenciado no projeto do Visual Studio, o arquivo. XML seja encontrado também. Arquivos de documentação XML não são necessários para o IntelliSense para funcionar com o código em um projeto ou em projetos referenciados por um projeto.  
  
 A menos que você compile com `/target:module`, o arquivo XML contém as marcas `<assembly></assembly>`. Essas marcas especificam o nome do arquivo que contém o manifesto do assembly para o arquivo de saída da compilação.  
  
 Ver [marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/index.md) maneiras de gerar documentação de comentários em seu código.  
  
|Para definir - doc no Visual Studio ambiente de desenvolvimento integrado|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Defina o valor na **arquivo de documentação XML gerar** caixa.|  
  
## <a name="example"></a>Exemplo  
 Ver [documentando seu código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) para obter um exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Documentando o Código com XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
