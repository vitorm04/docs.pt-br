---
title: "Para saber mais, confira Mitigação: cultura e operações assíncronas"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: debcae8281c832d2815e1b9896fbbcb725c8ffc3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-culture-and-asynchronous-operations"></a>Para saber mais, confira Mitigação: cultura e operações assíncronas
Em aplicativos direcionados ao [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] e versões posteriores, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> são armazenados no <xref:System.Threading.ExecutionContext> de um thread, que flui por operações assíncronas.  
  
## <a name="impact"></a>Impacto  
 Como resultado dessa alteração, alterações no <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> são refletidas nas tarefas que são executadas posteriormente de forma assíncrona. Isso é diferente do comportamento das versões anteriores do .NET Framework, que redefiniria <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> para o padrão do sistema em todas as tarefas assíncronas.  
  
## <a name="mitigation"></a>Redução  
 Os aplicativos afetados por essa alteração podem contorná-la de duas maneiras:  
  
-   Definindo explicitamente a propriedade <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> desejada como a primeira operação em uma tarefa assíncrona.  
  
-   Aceitando o comportamento antigo de não fluir <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> adicionando o seguinte elemento `AppContextSwitchOverrides` ao arquivo de configuração do aplicativo:  
  
    ```xml  
    <configuration>  
        <runtime>  
            <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
        </runtime>  
    </configuration>  
    ```  
  
-   Aceitando o comportamento antigo de não fluir <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> definindo a seguinte opção de compatibilidade de maneira programática:  
  
    ```csharp  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);  
    ```  
  
    ```vb  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true)  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

