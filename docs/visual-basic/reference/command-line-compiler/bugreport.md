---
title: /bugreport | Documentos do Microsoft
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
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: 22
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
ms.openlocfilehash: 9c64ec49d7e6842edbc0fed7407a34132a8f5a88
ms.lasthandoff: 03/13/2017

---
# <a name="bugreport"></a>/bugreport
Cria um arquivo que você pode usar quando o arquivo de um relatório de erros.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`file`|Necessário. O nome do arquivo que conterá o relatório de erros. Coloque o nome do arquivo entre aspas ("") se o nome contém um espaço.|  
  
## <a name="remarks"></a>Comentários  
 As informações a seguir são adicionadas ao `file`:  
  
-   Uma cópia de todos os arquivos de código-fonte na compilação.  
  
-   Uma lista das opções de compilador usado na compilação.  
  
-   Informações de versão sobre o compilador, o common language runtime e o sistema operacional.  
  
-   Compilador de saída, se houver.  
  
-   Uma descrição do problema, qual é solicitada.  
  
-   Uma descrição de como você acha que o problema deve ser corrigida, o que é solicitada.  
  
 Como uma cópia de todos os arquivos de código-fonte está incluída no `file`, talvez você queira reproduzir o defeito do código (suspeito) no programa mais curto possível.  
  
> [!IMPORTANT]
>  O `/bugreport` opção produz um arquivo que contém informações potencialmente confidenciais. Isso inclui a hora atual, a versão do compilador, [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] versão, versão do sistema operacional, nome de usuário, os argumentos de linha de comando com que o compilador foi executado, todo o código fonte, e o formulário binário de qualquer assembly referenciado. Essa opção pode ser acessada, especificando opções de linha de comando no arquivo Web. config para uma compilação do servidor de um [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] aplicativo. Para evitar isso, modifique o arquivo Machine. config para impedir os usuários de compilação no servidor.  
  
 Se essa opção for usada com `/errorreport:prompt`, `/errorreport:queue`, ou `/errorreport:send`, e o aplicativo encontra um erro interno do compilador, as informações no `file` é enviada à Microsoft Corporation. Essas informações ajudarão os engenheiros da Microsoft identificar a causa do erro e podem ajudar a melhorar a próxima versão do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Por padrão, nenhuma informação é enviada à Microsoft. No entanto, quando você compila um aplicativo usando `/errorreport:queue`, que é ativado por padrão, o aplicativo obtém seus relatórios de erros. Em seguida, quando o administrador do computador faz logon, o sistema de relatórios de erro exibe uma janela pop-up que permite que o administrador encaminhar à Microsoft relatórios de quaisquer erros que ocorreram desde o logon.  
  
> [!NOTE]
>  O `/bugreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente quando você compilar na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir compila `T2.vb` e coloca todas as informações de relatório de bugs no arquivo `Problem.txt`.  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [trustLevel elemento para securityPolicy (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/729ab04c-03da-4ee5-86b1-be9d08a09369)
