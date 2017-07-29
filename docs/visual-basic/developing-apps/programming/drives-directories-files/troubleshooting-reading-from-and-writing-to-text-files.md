---
title: "Solução de problemas: lendo e gravando em arquivos de texto (Visual Basic)"
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
- troubleshooting file I/O
- writing text to files, troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files, troubleshooting
- reading text files, troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: 10
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7f1d26df53445ee9711ebb2840071d2560c5380d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>Solução de problemas: lendo e gravando em arquivos de texto (Visual Basic)
Este tópico aborda problemas comuns encontrados ao trabalhar com arquivos de texto e sugere uma abordagem para cada um.  
  
## <a name="common-problems"></a>Problemas comuns  
 Os problemas mais comuns encontrados ao trabalhar com arquivos de texto incluem exceções de segurança, codificações de arquivo ou caminhos inválidos.  
  
### <a name="security-exceptions"></a>Exceções de segurança  
 A <xref:System.Security.SecurityException> é lançada quando ocorre um erro de segurança. Isso geralmente é um resultado do usuário não ter as permissões necessárias, o que pode ser resolvido adicionando permissões ou trabalhando com arquivos em um armazenamento isolado.  
  
### <a name="file-encodings"></a>Codificações de arquivo  
 As codificações de arquivo, também conhecidas como codificações de caracteres, especificam como representar caracteres no processamento de texto. Caracteres inesperados em um arquivo de texto podem resultar de uma codificação incorreta. Para a maioria dos arquivos, uma codificação pode ser preferível em relação a outra em termos de quais caracteres de idioma podem ou não ser manipulados, embora o Unicode geralmente seja o ideal. Para saber mais, confira [Codificações de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) e <xref:System.Text.Encoding>.  
  
### <a name="incorrect-paths"></a>Caminhos incorretos  
 Durante a análise de caminhos de arquivo, particularmente caminhos relativos, é fácil fornecer os dados errados. Muitos problemas podem ser corrigidos certificando-se de que está fornecendo o caminho correto. Para obter mais informações, consulte [Como analisar demarcadores de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 [Leitura de Arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Gravando em arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)   
 [Analisando arquivos de texto com o objeto TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)

