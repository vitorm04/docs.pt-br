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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1aee32c5c50c4ff4309f93bff270e6c3b3c8f7cc
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a>Mitigação: cultura e operações de dispatcher em aplicativos WPF
Em aplicativos direcionados ao .NET Framework 4.6 e ao .NET Framework 4.6.1, alterações nas propriedades <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> feitas dentro de um <xref:System.Windows.Threading.Dispatcher> são perdidas ao final da operação de dispatcher. Da mesma forma, as alterações em <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> feitas fora de uma operação de dispatcher podem não ser refletidas quando operação é executada.  
  
 Isso ocorre devido a uma alteração em <xref:System.Threading.ExecutionContext> que faz com que a <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sejam armazenadas no contexto de execução. As operações de dispatcher do WPF armazenam o contexto de execução usado para começar a operação e restaurar o contexto anterior quando a operação é concluída. Como <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> agora fazem parte desse contexto, alterações nelas em uma operação de dispatcher não são persistidas fora da operação.  
  
## <a name="impact"></a>Impacto  
 De modo prático, isso significa que alterações nas propriedades <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> podem não fluir entre os retornos de chamada da interface de usuário do WPF e outro código em um aplicativo WPF.  
  
## <a name="mitigation"></a>Redução  
 Os aplicativos afetados por essa alteração podem contorná-la de duas maneiras:  
  
-   Armazenando a <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> desejada em um campo e verificando em todos os corpos de operação de <xref:System.Windows.Threading.Dispatcher> (incluindo manipuladores de retorno de chamada de eventos da interface do usuário) se a <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> correta está definida.  
  
-   Como a alteração em <xref:System.Threading.ExecutionContext> afeta apenas aplicativos WPF direcionados ao .NET Framework 4.6 ou ao .NET Framework 4.6.1, essa alteração pode ser evitada direcionando ao .NET Framework 4.5.2 ou a uma versão do .NET Framework a partir da 4.6.2.  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
