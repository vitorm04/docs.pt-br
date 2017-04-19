---
title: "Para saber mais, confira Mitigação: cultura e operações assíncronas | Microsoft Docs"
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
ms.assetid: d2cdb578-9923-47df-9ffd-5865333ac1a4
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c2dbf60cacf47be3c448b5683b771840ef85ddaf
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-culture-and-asynchronous-operations"></a>Para saber mais, confira Mitigação: cultura e operações assíncronas
Para aplicativos direcionados ao [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] e versões posteriores, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> são armazenados em um <xref:System.Threading.ExecutionContext> do thread, que flui entre as operações assíncronas.  
  
## <a name="impact"></a>Impacto  
 Como resultado dessa mudança, as alterações em <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> serão refletidas em tarefas que são executadas posteriormente de forma assíncrona. Isso é diferente do comportamento de versões anteriores do .NET Framework, que redefiniriam <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> para o padrão do sistema em todas as tarefas assíncronas.  
  
## <a name="mitigation"></a>Redução  
 Os aplicativos afetados por essa alteração podem contorná-la de duas maneiras:  
  
-   Definindo explicitamente a propriedade <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> como a primeira operação em uma tarefa assíncrona.  
  
-   Aceitando o antigo comportamento de não deixar fluir <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> adicionando o seguinte elemento `AppContextSwitchOverrides` ao arquivo de configuração do aplicativo:  
  
    ```xml  
  
    <configuration>  
        <runtime>  
            <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
        </runtime>  
    </configuration>  
  
    ```  
  
-   Aceitando o antigo comportamento de não deixar fluir <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> configurando a seguinte opção de compatibilidade de forma programática:  
  
    ```csharp  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);  
    ```  
  
    ```vb  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true)  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
