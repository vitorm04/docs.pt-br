---
title: Formato inválido de área de transferência
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 5ec077be30b0afc8917d431dc9bd73c8dd41be89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649862"
---
# <a name="clipboard-format-is-not-valid"></a>Formato inválido de área de transferência
O formato da área de transferência especificado é incompatível com o método que está sendo executado. Entre as causas possíveis desse erro são:  
  
- Usando a área de transferência `GetText` ou `SetText` método com um formato de área de transferência diferente de `vbCFText` ou `vbCFLink`.  
  
- Usando a área de transferência `GetData` ou `SetData` método com um formato de área de transferência diferente de `vbCFBitmap`, `vbCFDIB`, ou `vbCFMetafile`.  
  
- Usando o `GetData` ou `SetData` métodos de um `DataObject` com um formato de área de transferência no intervalo reservado pelo Microsoft Windows para registrado formatos (& HC000 - HFFFF &), quando esse formato de área de transferência não foi registrado com o Microsoft Windows .  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova o formato inválido e especifique um válido.  
  
## <a name="see-also"></a>Consulte também

- [Área de transferência: adicionar outros formatos](/cpp/mfc/clipboard-adding-other-formats)
