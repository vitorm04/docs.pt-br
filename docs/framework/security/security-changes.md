---
title: "Alterações na segurança do .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
caps.latest.revision: 52
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b2ee4194f6e6788d99222badeb88e2702247904e
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="security-changes-in-the-net-framework"></a>Alterações na segurança do .NET Framework
A alteração mais importante para a segurança no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] é referente ao uso de nomenclatura forte. Consulte [Nomenclatura forte aprimorada](../../../docs/framework/app-domains/enhanced-strong-naming.md) para obter uma descrição dessas alterações.  
  
 O .NET Framework fornece um modelo de duas camadas de segurança para aplicativos gerenciados. Aplicativos [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] executados em um contêiner de segurança do Windows que limita o acesso aos recursos. Dentro desse contêiner, os aplicativos gerenciados são executados de modo totalmente confiável. De uma perspectiva de CAS (segurança de acesso de código), não há nada que um desenvolvedor possa fazer para elevar privilégios. Para obter informações sobre os privilégios concedidos pelo Windows, consulte [Declarações de funcionalidades do aplicativo (Aplicativos da Windows Store)](http://go.microsoft.com/fwlink/?LinkId=230436) no Centro de Desenvolvimento do Windows. Para obter informações sobre como criar um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo, consulte [Criar seu primeiro aplicativo da Windows Store usando C# ou Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).

