---
title: "Solucionando problemas: lendo e gravando em arquivos de texto (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "E/S [Visual Basic], solucionando problemas em arquivos de texto"
  - "lendo arquivos de texto, solucionando problemas"
  - "solucionando problemas em E/S de arquivo"
  - "solucionando problemas do Visual Basic, arquivos de texto"
  - "escrevendo texto em arquivos, solucionando problemas"
  - "escrevendo em arquivos, solucionando problemas"
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Solucionando problemas: lendo e gravando em arquivos de texto (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico aborda problemas encontrados ao trabalhar com arquivos de texto comuns e sugere uma abordagem para cada um desses problemas.  
  
## Problemas comuns  
 Os problemas mais comuns encontrados ao trabalhar com arquivos de texto inclui exceções de segurança, codificações de arquivo, ou caminhos inválidos.  
  
### Exceções de segurança  
 Uma <xref:System.Security.SecurityException> é acionada quando ocorre um erro de segurança.  Isso geralmente ocorre devido a um usuário sem permissões necessárias, e pode ser resolvido, adicionando permissões ou trabalhando com arquivos em um armazenamento isolado.  Para obter mais informações, consulte [Exceções de solução de problemas: System.Security.SecurityException](../Topic/Troubleshooting%20Exceptions:%20System.Security.SecurityException.md).  
  
### Codificação de Arquivos  
 Codificações de arquivo, também conhecido como codificações de caracteres, especificam como deseja representar caracteres quando estiver processando um texto.  Caracteres inesperados em um arquivo de texto podem resultar de uma codificação incorreta.  Para a maioria dos arquivos, uma codificação pode ser preferível sobre outra em termos de quais caracteres de idioma ele pode ou não pode tratar, embora Unicode seja geralmente preferido.  Para obter mais informações, consulte [Codificações de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) e <xref:System.Text.Encoding>.  
  
### Caminhos Incorretos  
 Quando se está analisando caminhos de arquivo, particularmente caminhos relativos, é fácil fornecer os dados errados.  Muitos problemas podem ser corrigidos, certificando\-se se você está fornecendo o caminho correto.  Para obter mais informações, consulte [Como analisar caminhos de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 [Lendo a partir de arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Gravando em arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)   
 [Analisando arquivos de texto com o objeto TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)