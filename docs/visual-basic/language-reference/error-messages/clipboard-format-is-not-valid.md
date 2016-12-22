---
title: "Formato inv&#225;lido de &#225;rea de transfer&#234;ncia | Microsoft Docs"
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
  - "vbrID460"
dev_langs: 
  - "VB"
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Formato inv&#225;lido de &#225;rea de transfer&#234;ncia
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O formato da Área de transferência especificado é incompatível com o método que está sendo executado.  Entre as causas possíveis para esse erro estão:  
  
-   Usando o método `GetText` ou `SetText` da área de transferência com um formato da área de transferência diferente de `vbCFText` ou `vbCFLink`.  
  
-   Usando a área de transferência `GetData` ou `SetData` método com um formato de área de transferência diferente de `vbCFBitmap`, `vbCFDIB`, ou `vbCFMetafile`.  
  
-   Usando o método `DataObject` `GetData` ou o método `SetData` com um formato da Área de transferência no intervalo reservado pelo Microsoft Windows para formatos registrados \(& HC000 \- HFFFF &\), quando esse formato da Área de transferência não foi registrado com o Microsoft Windows.  
  
### Para corrigir este erro  
  
-   Remova o formato inválido e especifique um válido.  
  
## Consulte também  
 [Área de Transferência: adicionando outros formatos](../Topic/Clipboard:%20Adding%20Other%20Formats.md)