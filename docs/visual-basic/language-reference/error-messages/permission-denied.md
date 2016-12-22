---
title: "Permiss&#227;o negada (Visual Basic) | Microsoft Docs"
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
  - "vbrID70"
dev_langs: 
  - "VB"
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Permiss&#227;o negada (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Houve uma tentativa para gravar em um disco protegido contra gravação ou para acessar um arquivo bloqueado.  
  
### Para corrigir este erro  
  
1.  Para abrir um arquivo protegido contra gravação, altere o atributo proteção contra gravação do arquivo.  
  
2.  Certifique\-se que outro processo não bloqueou o arquivo,  e esperer para abrir o arquivo até que o outro processo o libere.  
  
3.  Para acessar o registro, verifique se as permissões de usuário incluem esse tipo de acesso ao Registro.  
  
## Consulte também  
 [Tipos de erro](../../../visual-basic/programming-guide/language-features/error-types.md)