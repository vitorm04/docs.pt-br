---
title: "Instru&#231;&#227;o Error | Microsoft Docs"
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
  - "vb.error"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Error"
  - "instrução Error"
  - "instrução Error, sintaxe"
  - "erros [Visual Basic], simulando"
  - "erros de tempo de execução, códigos"
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Error
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Simula a ocorrência de um erro.  
  
## Sintaxe  
  
```  
Error errornumber  
```  
  
## Partes  
 `errornumber`  
 Obrigatório.  Pode ser qualquer número de erro válido.  
  
## Comentários  
 A instrução `Error`é suportada para compatibilidade com versões anteriores.  No novo código, especialmente ao criar objetos, use o método `Raise` do objeto `Err` para gerar erros de tempo de execução.  
  
 Se `errornumber` estiver definida, a declaração `Error` chama o manipulador de erro após as propriedades do objeto `Err` são os seguintes valores padrão atribuídas:  
  
|Propriedade|Valor|  
|-----------------|-----------|  
|`Number`|Valor especificado como argumento para declaração `Error`.  Pode ser qualquer número de erro válido.|  
|`Source`|Nome do projeto Visual Basic atual.|  
|`Description`|Sequência expressão correspondente a valor de retorno da função `Error` para o `Number` especificado, se houver essa sequência de caracteres.  Se a sequência de caracteres não existir, `Description` contém uma cadeia de caracteres de comprimento nulo \(" "\).|  
|`HelpFile`|A unidade, caminho e nome de arquivo totalmente qualificados do arquivo da Ajuda Visual Basic.|  
|`HelpContext`|A identificação do contexto do arquivo da ajuda Visual Basic para o erro correspondente à propriedade `Number`.|  
|`LastDLLError`|Zero.|  
  
 Se nenhum manipulador de erro existe, ou se nenhum está ativado, uma mensagem de erro é criada e exibida das propriedades do objeto `Err`.  
  
> [!NOTE]
>  Alguns aplicativos host Visual Basic não podem criar objetos.  Consulte sua documentação do aplicativo host para determinar se ele pode criar classes e objetos.  
  
## Exemplo  
 Este exemplo usa a declaração `Error` para gerar o erro número 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## Requisitos  
 **Namespace:** [VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** Visual Basic Runtime Library \(in Microsoft.VisualBasic.dll\)  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>   
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>   
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Mensagens de erro](../../../visual-basic/language-reference/error-messages/index.md)