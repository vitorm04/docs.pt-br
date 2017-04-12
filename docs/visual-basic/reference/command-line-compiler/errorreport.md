---
title: /errorreport | Documentos do Microsoft
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
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2ebe5646256926f68a1a900b91c25a1768505785
ms.lasthandoff: 03/13/2017

---
# <a name="errorreport"></a>/errorreport
Especifica como o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador deve relatar erros do compilador interno.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>Comentários  
 Essa opção fornece uma maneira conveniente para relatar um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] erro interno do compilador (ICE) para o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] equipe da Microsoft. Por padrão, o compilador não envia informações à Microsoft. No entanto, se você encontrar um erro interno do compilador, esta opção permite que você relate o erro à Microsoft. Essas informações ajudarão os engenheiros da Microsoft identificar a causa e podem ajudar a melhorar a próxima versão do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 A capacidade do usuário para enviar relatórios depende de permissões de política de máquina e usuário.  
  
 A tabela a seguir resume o efeito de `/errorreport` opção.  
  
|Opção|Comportamento|  
|---|---|  
|`prompt`|Se ocorrer um erro interno do compilador, uma caixa de diálogo aparece para que você possa exibir os dados exatos que o compilador coletado. Você pode determinar se há informações confidenciais no relatório de erro e tomar uma decisão sobre se deseja enviá-lo à Microsoft. Se você optar por enviá-lo, e as configurações de diretiva de computador e usuário permitirem, o compilador envia os dados à Microsoft.|  
|`queue`|Enfileira o relatório de erros. Quando você efetuar logon com privilégios de administrador, você pode relatar falhas desde a última vez em que você estava conectado (você não precisará enviar relatórios de falhas mais de uma vez a cada três dias). Esse é o comportamento padrão quando o `/errorreport` opção não for especificada.|  
|`send`|Se ocorrer um erro interno do compilador, e as configurações de diretiva de computador e usuário permitirem, o compilador envia os dados à Microsoft.<br /><br /> A opção `/errorReport:send` tenta enviar automaticamente informações de erro à Microsoft. Essa opção depende do registro. Para obter mais informações sobre como definir os valores apropriados no registro, consulte [como ativar o relatório de erros automático em ferramentas de linha de comando do Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695).|  
|`none`|Se ocorrer um erro interno do compilador, ele será não ser coletado ou enviado à Microsoft.|  
  
 O compilador envia os dados que incluem a pilha no momento do erro, que geralmente inclui algum código-fonte. Se `/errorreport` é usado com o [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, o arquivo de origem inteiro é enviado.  
  
 Essa opção é melhor usada com a [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, pois permite que os engenheiros da Microsoft mais facilmente reproduzir o erro.  
  
> [!NOTE]
>  O `/errorreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir tenta compilar `T2.vb`, e se o compilador encontrar um erro interno do compilador, ele solicitará que você envie o relatório de erros à Microsoft.  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
