---
title: Alterações na segurança do .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af2869e5ca3b41778c094b7a78a9493e74868811
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204502"
---
# <a name="security-changes-in-the-net-framework"></a>Alterações na segurança do .NET Framework

The most important change to security in the .NET Framework 4.5 is in strong naming. Consulte [Nomenclatura forte aprimorada](../../standard/assembly/enhanced-strong-naming.md) para obter uma descrição dessas alterações.  
  
O .NET Framework fornece um modelo de duas camadas de segurança para aplicativos gerenciados. Windows 8.x Store apps run in a Windows security container that limits access to resources. Dentro desse contêiner, os aplicativos gerenciados são executados de modo totalmente confiável. De uma perspectiva de CAS (segurança de acesso de código), não há nada que um desenvolvedor possa fazer para elevar privilégios. Para obter informações sobre os privilégios concedidos pelo Windows, consulte [Declarações de funcionalidades do aplicativo (Aplicativos da Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) no Centro de Desenvolvimento do Windows. For information about creating a Windows 8.x Store app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).
