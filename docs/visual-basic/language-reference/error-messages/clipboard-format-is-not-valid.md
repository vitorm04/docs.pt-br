---
title: "Formato inválido de área de transferência"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="clipboard-format-is-not-valid"></a>Formato inválido de área de transferência
O formato de área de transferência especificado é incompatível com o método que está sendo executado. Entre as causas possíveis desse erro são:  
  
-   Usando a área de transferência `GetText` ou `SetText` método com um formato de área de transferência diferente de `vbCFText` ou `vbCFLink`.  
  
-   Usando a área de transferência `GetData` ou `SetData` método com um formato de área de transferência diferente de `vbCFBitmap`, `vbCFDIB`, ou `vbCFMetafile`.  
  
-   Usando o `DataObject``GetData` método ou `SetData` método com um formato de área de transferência no intervalo reservado pelo Microsoft Windows para registrado formatos (& HC000 - HFFFF &), quando esse formato de área de transferência não foi registrado com o Microsoft Windows.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova o formato inválido e especifique um válido.  
  
## <a name="see-also"></a>Consulte também  
 [Área de transferência: adicionando outros formatos](/cpp/mfc/clipboard-adding-other-formats)
