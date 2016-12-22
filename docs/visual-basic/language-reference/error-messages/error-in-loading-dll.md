---
title: "Erro no carregamento da DLL (Visual Basic) | Microsoft Docs"
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
  - "vbrID48"
dev_langs: 
  - "VB"
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Erro no carregamento da DLL (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma biblioteca de vínculo dinâmico \(DLL\) é uma biblioteca especificada na cláusula `Lib` de uma `Declare` instrução.  Possíveis causas do erro incluem:  
  
-   O arquivo é não dll executável.  
  
-   O arquivo é não uma DLL do Microsoft Windows.  
  
-   A DLL referências outro DLL que não está presente.  
  
-   A DLL ou referenciado DLL não está em um diretório especificado no caminho.  
  
### Para corrigir este erro  
  
-   Se o arquivo for uma fonte \- arquivo de texto e, portanto, não dll executável, ele deve ser compilado e vinculado a um formulário dll\-executável.  
  
-   Se o arquivo for Não uma DLL do Microsoft Windows, obtenha o Microsoft Windows equivalente.  
  
-   Se a DLL referências outro DLL que não está presente, obter a dll de referência e disponibilizá\-lo.  
  
-   Se a DLL ou DLL referenciado não estiver em um diretório especificado pelo caminho, mova a DLL para um diretório referenciado.  
  
## Consulte também  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)