---
title: "Instru&#231;&#227;o End | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.End"
  - "End"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "código, saindo"
  - "palavra-chave End, instruções End"
  - "instrução End"
  - "execução, terminando"
  - "execução, parando"
  - "arquivos, fechamento"
  - "encerramento do programa"
  - "programas, saindo"
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o End
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Finaliza a execução imediatamente.  
  
## Sintaxe  
  
```  
End  
```  
  
## Comentários  
 Você pode colocar o `End` a instrução em qualquer lugar em um procedimento para forçar o aplicativo inteiro para interromper a execução.  `End`Fecha todos os arquivos abertos com um `Open` instrução e limpa as variáveis de todos os do aplicativo.  O aplicativo fecha assim que não existirem outros programas que contenham referências a seus objetos e nenhum dos seu código esteja sendo executado.  
  
> [!NOTE]
>  A instrução `End` interrompe a execução de código abruptamente e não chama os métodos `Dispose` ou `Finalize` ou qualquer outro código Visual Basic.  Referências a objetos mantidas por outros programas são invalidadas.  Se uma instrução `End` for encontrada em um bloco `Try` ou `Catch`, o controle não passa para o bloco `Finally` correspondente.  
  
 A instrução `Stop` suspende a execução, mas diferentemente de `End`, não fecha os arquivos nem desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável \(.exe\) compilado.  
  
 Como `End` encerra o aplicativo se preocupar com quaisquer recursos que possam estar abertos, você deve tentar fechar o aplicativo corretamente antes de usá\-lo.  Por exemplo, se seu aplicativo tiver qualquer formulário aberto, você deve fechá\-lo antes de o controle atingir a instrução `End`.  
  
 Você deve usar `End` com parcimônia e somente quando você precisa parar imediatamente.  As maneiras normais para encerrar um procedimento \([Instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) e [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)\) não apenas o fecham corretamente, mas também fornecem ao código de chamada a oportunidade para finalizar corretamente.  Um aplicativo de console, por exemplo, pode simplesmente `Return` do procedimento `Main`.  
  
> [!IMPORTANT]
>  O `End` chamadas de instrução a <xref:System.Environment.Exit%2A> método da <xref:System.Environment> classe na <xref:System> espaço para nome.  <xref:System.Environment.Exit%2A>requer que você tenha `UnmanagedCode` permissão.  Se você não fizer isso, ocorrerá um erro <xref:System.Security.SecurityException>.  
  
 Quando seguido por uma palavra\-chave adicional, [Instrução End \<keyword\>](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineia o final da definição do procedimento ou bloco apropriado.  Por exemplo, `End Function` termina a definição de um procedimento `Function`.  
  
## Exemplo  
 O exemplo a seguir utiliza a instrução `End` para encerrar a execução de código se o usuário solicitar.  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## Anotações Developer Dispositivo Inteligente  
 Não há suporte para essa instrução.  
  
## Consulte também  
 <xref:System.Security.Permissions.SecurityPermissionFlag>   
 [Instrução Stop](../../../visual-basic/language-reference/statements/stop-statement.md)   
 [Instrução End \<keyword\>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)