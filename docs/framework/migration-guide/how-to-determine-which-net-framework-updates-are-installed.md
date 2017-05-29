---
title: "Como determinar quais atualizações do .NET Framework estão instaladas | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: 6
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: 6237bdaf1d12743bee71633acf8cef69c21b414e
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="how-to-determine-which-net-framework-updates-are-installed"></a>Como determinar quais atualizações do .NET Framework estão instaladas
As atualizações instaladas para cada versão do .NET Framework instalado em um computador estão listadas no Registro do Windows. Você pode usar o Editor do Registro (regedit.exe) para exibir essas informações.  
  
 No Editor do Registro, as versões do .NET Framework e as atualizações instaladas para cada versão são armazenadas em subchaves diferentes. Para saber mais sobre como detectar os números da versão instalada, veja [Como determinar quais versões do .NET Framework estão instaladas](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md). Para saber mais sobre como instalar o .NET Framework, veja o [Guia de instalação](../../../docs/framework/install/guide-for-developers.md).  
  
### <a name="to-find-installed-updates"></a>Para localizar atualizações instaladas  
  
1.  Abra o programa **regedit.exe**. No Windows 8 e superior abra a tela Iniciar e digite o nome. Em versões anteriores do Windows, no menu **Iniciar**, escolha **Executar** e, na caixa **Abrir**, digite **regedit.exe**.  
  
     Você deve ter credenciais administrativas para executar o regedit.exe.  
  
2.  No Editor do Registro, abrir a seguinte subchave:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates  
  
     As atualizações instaladas estão listadas nas subchaves que identificam a versão do .NET Framework a que se aplicam. Cada atualização é identificada por um número da Base de Dados de Conhecimento (KB).  
  
## <a name="example"></a>Exemplo  
 O código a seguir determina programaticamente as atualizações do .NET Framework instaladas em um computador. Você precisa ter as credenciais administrativas para executar esse exemplo.  
  
 [!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)] [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]  
  
 O exemplo produz uma saída semelhante à seguinte:  
  
```  
  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como determinar quais versões do .NET Framework estão instaladas](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
 [Guia de instalação](../../../docs/framework/install/guide-for-developers.md)   
 [Versões e dependências](../../../docs/framework/migration-guide/versions-and-dependencies.md)

