---
title: Formato inválido de área de transferência
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 429d1e120a0044152a358a87663eb09989f45b0e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874586"
---
# <a name="clipboard-format-is-not-valid"></a>Formato inválido de área de transferência

O formato da área de transferência especificado é incompatível com o método que está sendo executado. Entre as possíveis causas desse erro estão:  
  
- Usando o método ou da área de transferência `GetText` `SetText` com um formato de área de transferência diferente de `vbCFText` ou `vbCFLink` .  
  
- Usando o método ou da área de transferência `GetData` `SetData` com um formato de área de transferência diferente de `vbCFBitmap` , `vbCFDIB` ou `vbCFMetafile` .  
  
- Usando os `GetData` `SetData` métodos ou de um `DataObject` com um formato de área de transferência no intervalo reservado pelo Microsoft Windows para formatos registrados (&HC000-&HFFFF), quando esse formato de área de transferência não foi registrado no Microsoft Windows.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova o formato inválido e especifique um válido.  
  
## <a name="see-also"></a>Confira também

- [Área de transferência: adicionando outros formatos](/cpp/mfc/clipboard-adding-other-formats)
