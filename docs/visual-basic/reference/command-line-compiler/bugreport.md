---
title: "/bugreport | Microsoft Docs"
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
  - "Opção de compilador /bugreport [Visual Basic]"
  - "Opção de compilador bugreport [Visual Basic]"
  - "Opção de compilador -bugreport [Visual Basic]"
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /bugreport
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cria um arquivo que pode ser usado quando você arquivar um relatório de erros.  
  
## Sintaxe  
  
```  
/bugreport:file  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`file`|Obrigatório.  O nome do arquivo que conterá seu relatório de bug.  Coloque o nome do arquivo entre aspas \(""\) se o nome contém um espaço.|  
  
## Comentários  
 As informações a seguir são adicionadas ao `file`:  
  
-   Uma cópia de todos os arquivos de código\-fonte em que a compilação.  
  
-   Uma lista de opções do compilador usadas na compilação.  
  
-   Informações de versão sobre seu compilador, o common language runtime e o sistema operacional.  
  
-   Compilador de saída, se houver.  
  
-   Uma descrição do problema, para o qual você é solicitado.  
  
-   Uma descrição de como você acha que o problema deve ser corrigida, para os quais você é solicitado.  
  
 Porque uma cópia de todos os arquivos de código\-fonte está incluída no `file`, talvez você queira reproduzir o defeito de código \(suspeito\) no programa mais curto possível.  
  
> [!IMPORTANT]
>  O `/bugreport` opção produz um arquivo que contém informações potencialmente confidenciais.  Isso inclui a hora atual, a versão do compilador, [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] versão, versão do sistema operacional, nome de usuário, os argumentos de linha de comando com o qual o compilador foi executado, todo o código fonte, e o formato binário de qualquer referência de assembly.  Esta opção pode ser acessada, especificando opções de linha de comando no arquivo Web. config para uma compilação do lado do servidor de um [!INCLUDE[vstecasp](../../../visual-basic/developing-apps/programming/drives-directories-files/includes/vstecasp_md.md)] aplicativo.  Para evitar isso, modifique o arquivo Machine. config para impedir os usuários de compilação no servidor.  
  
 Se esta opção for usada com `/errorreport:prompt`, `/errorreport:queue`, ou `/errorreport:send`, e o seu aplicativo encontra um erro interno do compilador, as informações em `file` é enviada à Microsoft Corporation.  Essa informação ajudará os engenheiros da Microsoft a identificar a causa do erro e pode ajudar a melhorar a próxima versão do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Por padrão, nenhuma informação é enviada à Microsoft.  No entanto, quando você compila um aplicativo usando `/errorreport:queue`, que é ativado por padrão, o aplicativo obtém seus relatórios de erro.  Em seguida, quando o administrador do computador faz logon, o sistema de relatórios de erro exibe uma janela pop\-up que permite que o administrador encaminhar à Microsoft relatórios de quaisquer erros que ocorreram desde o logon.  
  
> [!NOTE]
>  O `/bugreport` opção não está disponível no ambiente de desenvolvimento Visual Studio; ele está disponível somente quando você compilar na linha de comando.  
  
## Exemplo  
 O exemplo a seguir compila `T2.vb` e coloca todas as informações do serviço de relato de erros no arquivo `Problem.txt`.  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/debug](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [\/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [trustLevel elemento para securityPolicy \(ASP.NET Settings Schema\)](http://msdn.microsoft.com/pt-br/729ab04c-03da-4ee5-86b1-be9d08a09369)