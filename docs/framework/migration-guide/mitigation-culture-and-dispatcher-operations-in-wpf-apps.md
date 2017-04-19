---
title: "Mitigação: cultura e operações de dispatcher em aplicativos WPF | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 455c1452-8ce0-45ae-a092-21fb8edf1cac
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1aee32c5c50c4ff4309f93bff270e6c3b3c8f7cc
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a>Mitigação: cultura e operações de dispatcher em aplicativos WPF
Em aplicativos direcionados ao .NET Framework 4.6 e ao .NET Framework 4.6.1, as alterações nas propriedades <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> que são feitas em um <xref:System.Windows.Threading.Dispatcher> são perdidas no fim dessa operação de dispatcher. De modo semelhante, as alterações em <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> feitas fora de uma operação de dispatcher podem não ser refletidas quando essa operação for executada.  
  
 Isso ocorre devido a uma alteração no <xref:System.Threading.ExecutionContext> que faz com que o <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sejam armazenados no contexto de execução. As operações de dispatcher do WPF armazenam o contexto de execução usado para começar a operação e restaurar o contexto anterior quando a operação é concluída. Como <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> agora fazem parte desse contexto, as alterações feitas neles dentro de uma operação de dispatcher não persistem fora da operação.  
  
## <a name="impact"></a>Impacto  
 Em termos práticos, isso significa que as alterações nas propriedades <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> podem não fluir entre os retornos de chamada da interface do usuário do WPF e outro código em um aplicativo WPF.  
  
## <a name="mitigation"></a>Redução  
 Os aplicativos afetados por essa alteração podem contorná-la de duas maneiras:  
  
-   Armazenando o <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> desejado em um campo e verificando em todos os corpos de operação <xref:System.Windows.Threading.Dispatcher> (incluindo manipuladores de retorno de chamada de eventos da interface do usuário) se o <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> correto está definido.  
  
-   Como a alteração <xref:System.Threading.ExecutionContext> afeta apenas aplicativos WPF destinados ao .NET Framework 4.6 ou .NET Framework 4.6.1, essa alteração pode ser evitada direcionando ao .NET Framework 4.5.2 ou uma versão do .NET Framework a partir da 4.6.2.  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
