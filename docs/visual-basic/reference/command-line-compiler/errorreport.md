---
title: "-errorreport | Microsoft Docs"
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
  - "Opção de compilador -errorreport [Visual Basic]"
  - "Opção de compilador /errorreport [Visual Basic]"
  - "Opção de compilador errorreport [Visual Basic]"
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /errorreport
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica como o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador deve relatar erros do compilador interno.  
  
## Sintaxe  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## Comentários  
 Essa opção fornece uma maneira conveniente para relatar um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] erro interno do compilador \(ICE\) para o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] equipe da Microsoft. Por padrão, o compilador não envia informações à Microsoft. No entanto, se você encontrar um erro interno do compilador, esta opção permite que você relate o erro à Microsoft. Essas informações ajudarão os engenheiros da Microsoft identificar a causa e podem ajudar a melhorar a próxima versão do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 A capacidade do usuário para enviar relatórios depende de permissões de política de máquina e usuário.  
  
 A tabela a seguir resume o efeito de `/errorreport` opção.  
  
|||  
|-|-|  
|Opção|Comportamento|  
|`prompt`|Se ocorrer um erro interno do compilador, uma caixa de diálogo aparece para que você possa exibir os dados exatos que o compilador coletado. Você pode determinar se há informações confidenciais no relatório de erro e tomar uma decisão sobre se deseja enviá\-lo à Microsoft. Se você optar por enviá\-lo, e as configurações de diretiva de computador e usuário permitirem, o compilador envia os dados à Microsoft.|  
|`queue`|Enfileira o relatório de erros. Quando você efetuar logon com privilégios de administrador, você pode relatar falhas desde a última vez em que você estava conectado \(você não precisará enviar relatórios de falhas mais de uma vez a cada três dias\). Esse é o comportamento padrão quando o `/errorreport` opção não for especificada.|  
|`send`|Se ocorrer um erro interno do compilador, e as configurações de diretiva de computador e usuário permitirem, o compilador envia os dados à Microsoft.<br /><br /> A opção `/errorReport:send` tenta enviar automaticamente informações de erro à Microsoft. Essa opção depende do registro. Para obter mais informações sobre como definir os valores apropriados no registro, consulte [como ativar o relatório de erros automático em ferramentas de linha de comando do Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695).|  
|`none`|Se ocorrer um erro interno do compilador, ele será não ser coletado ou enviado à Microsoft.|  
  
 O compilador envia os dados que incluem a pilha no momento do erro, que geralmente inclui algum código\-fonte. Se `/errorreport` é usado com o [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, o arquivo de origem inteiro é enviado.  
  
 Essa opção é melhor usada com a [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, pois permite que os engenheiros da Microsoft mais facilmente reproduzir o erro.  
  
> [!NOTE]
>  O `/errorreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## Exemplo  
 O código a seguir tenta compilar `T2.vb`, e se o compilador encontrar um erro interno do compilador, ele solicitará que você envie o relatório de erros à Microsoft.  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)