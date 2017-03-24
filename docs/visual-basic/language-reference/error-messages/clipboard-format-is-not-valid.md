---
title: "Formato da área de transferência não é válido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID460
dev_langs:
- VB
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: eadbd679dbe80c17979f328737531e14898af368
ms.lasthandoff: 03/13/2017

---
# <a name="clipboard-format-is-not-valid"></a>Formato inválido de área de transferência
O formato da área de transferência especificado é incompatível com o método que está sendo executado. Entre as possíveis causas para esse erro são:  
  
-   Usando a área de transferência `GetText` ou `SetText` método com um formato da área de transferência diferente de `vbCFText` ou `vbCFLink`.  
  
-   Usando a área de transferência `GetData` ou `SetData` método com um formato da área de transferência diferente de `vbCFBitmap`, `vbCFDIB`, ou `vbCFMetafile`.  
  
-   Usando o `DataObject``GetData` método ou `SetData` método com um formato da área de transferência no intervalo reservado pelo Microsoft Windows para formatos registrados (< / HC000-< / HFFFF), quando esse formato da área de transferência não foi registrado com o Microsoft Windows.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova o formato inválido e especifique um válido.  
  
## <a name="see-also"></a>Consulte também  
 [Área de transferência: adicionando outros formatos](http://msdn.microsoft.com/library/aea58159-65ed-4385-aeaa-3d9d5281903b)
