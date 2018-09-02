---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: e8366e1050217f3d993d510683252728aba0c3d9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452642"
---
# <a name="-bugreport"></a>-bugreport
Cria um arquivo que você pode usar quando você arquiva um relatório de bugs.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`file`|Necessário. O nome do arquivo que conterá o relatório de bug. Coloque o nome do arquivo entre aspas ("") se o nome contiver um espaço.|  
  
## <a name="remarks"></a>Comentários  
 As informações a seguir são adicionadas ao `file`:  
  
-   Uma cópia de todos os arquivos de código-fonte na compilação.  
  
-   Uma lista das opções do compilador usado na compilação.  
  
-   Informações de versão sobre seu compilador, o common language runtime e o sistema operacional.  
  
-   Saída do compilador, se houver.  
  
-   Uma descrição do problema, para o qual você será solicitado.  
  
-   Uma descrição de como você acha que o problema deve ser corrigida, para o qual você será solicitado.  
  
 Como uma cópia de todos os arquivos de código-fonte está incluída no `file`, talvez você queira reproduzir o defeito do código (suspeito) no programa mais curto possível.  
  
> [!IMPORTANT]
>  O `-bugreport` opção produz um arquivo que contém informações potencialmente confidenciais. Isso inclui a hora atual, a versão do compilador [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] versão, versão do sistema operacional, nome de usuário, os argumentos de linha de comando com a qual o compilador foi executado, todo código-fonte, e o formulário binário de qualquer um de assembly referenciado. Essa opção pode ser acessada, especificando opções de linha de comando no arquivo Web. config para uma compilação do lado do servidor de um [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplicativo. Para evitar isso, modifique o arquivo Machine. config para impedir que os usuários no servidor de compilação.  
  
 Se essa opção é usada com `-errorreport:prompt`, `-errorreport:queue`, ou `-errorreport:send`, e o seu aplicativo encontra um erro interno do compilador, as informações no `file` é enviada à Microsoft Corporation. Essas informações ajudam os engenheiros da Microsoft a identificar a causa do erro e podem ajudar a melhorar a próxima versão do Visual Basic. Por padrão, nenhuma informação é enviada à Microsoft. No entanto, quando você compila um aplicativo usando `-errorreport:queue`, que é habilitado por padrão, o aplicativo obtém seus relatórios de erros. Em seguida, quando o administrador do computador faz logon, o sistema de relatórios de erro exibe uma janela pop-up que permite que o administrador encaminhar à Microsoft relatórios de quaisquer erros que ocorreram desde o logon.  
  
> [!NOTE]
>  O `/bugreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando você compila da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir compila `T2.vb` e coloca todas as informações de relatório de bugs no arquivo `Problem.txt`.  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [trustLevel elemento para securityPolicy (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)
