---
title: '{1&gt;Informações do sistema&lt;1}'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
ms.openlocfilehash: a91e2fd8db0ef338ce30f89f11869f1b6698af3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732583"
---
# <a name="system-information-and-windows-forms"></a>Informações do sistema e o Windows Forms
Às vezes, é necessário obter informações sobre o computador em que o aplicativo está sendo executado para tomar decisões em seu código. Por exemplo, você pode ter uma função que só é aplicável quando conectada a um domínio de rede específico; Nesse caso, você precisaria de uma maneira de determinar o domínio e desabilitar a função se o domínio não estiver presente.  
  
 Windows Forms aplicativos podem usar a classe <xref:System.Windows.Forms.SystemInformation> para determinar várias coisas sobre um computador em tempo de execução. O exemplo a seguir demonstra como usar a classe <xref:System.Windows.Forms.SystemInformation> para recuperar o <xref:System.Windows.Forms.SystemInformation.UserName%2A> e <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to "
+ Domain);
```  
  
 Todos os membros da classe <xref:System.Windows.Forms.SystemInformation> são somente leitura; Não é possível modificar as configurações de um usuário. Há mais de 100 membros da classe, retornando informações sobre tudo, desde o número de monitores anexados ao computador (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) até o espaçamento de ícones no Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> e <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).  
  
 Alguns dos membros mais úteis da classe <xref:System.Windows.Forms.SystemInformation> incluem <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>e <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.SystemInformation>
- [Gerenciamento de Energia nos Windows Forms](power-management-in-windows-forms.md)
