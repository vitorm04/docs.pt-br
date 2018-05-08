---
title: Formato inválido de área de transferência
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: eef16096b269902dbaca6a344abf4c5f6a504fb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
