---
title: 'Mitigação: Implementações personalizadas de IMessageFilter.PreFilterMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af81468c5c4c4caf2f09725d6c7c4723084e35c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779436"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="1afed-102">Mitigação: Implementações personalizadas de IMessageFilter.PreFilterMessage</span><span class="sxs-lookup"><span data-stu-id="1afed-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="1afed-103">Em aplicativos do Windows Forms direcionados a versões do .NET Framework começando com o .NET Framework 4.6.1, uma implementação de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> personalizada pode filtrar mensagens quando o método <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> for chamado se a implementação <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="1afed-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="1afed-104">Executa uma ou ambas as ações:</span><span class="sxs-lookup"><span data-stu-id="1afed-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="1afed-105">Adiciona um filtro de mensagem chamando o método <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="1afed-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="1afed-106">Remove um filtro de mensagem chamando o método <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="1afed-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="1afed-107">método.</span><span class="sxs-lookup"><span data-stu-id="1afed-107">method.</span></span>

- <span data-ttu-id="1afed-108">**E** bombeia mensagens chamando o método <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1afed-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="1afed-109">Impacto</span><span class="sxs-lookup"><span data-stu-id="1afed-109">Impact</span></span>

<span data-ttu-id="1afed-110">Essa alteração afeta somente os aplicativos do Windows Forms que se destinam a versões do .NET Framework, começando pelo .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="1afed-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="1afed-111">Para aplicativos do Windows Forms direcionados a versões anteriores do .NET Framework, essas implementações podem, em alguns casos, lançar uma exceção <xref:System.IndexOutOfRangeException> quando o método <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> é chamado</span><span class="sxs-lookup"><span data-stu-id="1afed-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="1afed-112">Redução</span><span class="sxs-lookup"><span data-stu-id="1afed-112">Mitigation</span></span>

<span data-ttu-id="1afed-113">Se essa alteração for indesejável, aplicativos que se destinarem ao .NET Framework 4.6.1 ou a uma versão posterior poderão recusá-la adicionando a seguinte definição de configuração à seção [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="1afed-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="1afed-114">Além disso, os aplicativos destinados a versões anteriores do .NET Framework, mas que estão sendo executados no .NET Framework 4.6.1 ou em uma versão posterior, podem aceitar esse comportamento adicionando a seguinte definição de configuração à seção [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="1afed-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="1afed-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1afed-115">See also</span></span>

- [<span data-ttu-id="1afed-116">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="1afed-116">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
