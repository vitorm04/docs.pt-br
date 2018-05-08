---
title: Como determinar a versão instalada do WPF
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: c59fa0d0a4d94c6e6a2ab72a4cd7a3c066649fb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Como determinar a versão instalada do WPF
O número de versão para a versão atual instalada do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] está localizado no **registro**.  
  
 Para localizar o número de versão:  
  
1.  No menu **Iniciar** , clique em **Executar**.  
  
2.  Em **abrir**, tipo **regedit.exe**.  
  
3.  Abra a seguinte chave:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o número de versão é armazenado no **versão** valor.
