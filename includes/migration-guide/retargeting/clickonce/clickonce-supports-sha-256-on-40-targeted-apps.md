---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804605"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="02eb4-101">ClickOnce é compatível com SHA-256 em aplicativos destinados ao 4.0</span><span class="sxs-lookup"><span data-stu-id="02eb4-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

|   |   |
|---|---|
|<span data-ttu-id="02eb4-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="02eb4-102">Details</span></span>|<span data-ttu-id="02eb4-103">Anteriormente, um aplicativo ClickOnce com um certificado assinado com SHA-256 exigia a presença do .NET Framework 4.5 ou posterior, mesmo se o aplicativo fosse direcionado ao 4.0.</span><span class="sxs-lookup"><span data-stu-id="02eb4-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="02eb4-104">Agora, os aplicativos ClickOnce direcionados ao .NET Framework 4.0 podem ser executados no .NET Framework 4.0, mesmo quando assinados com SHA-256.</span><span class="sxs-lookup"><span data-stu-id="02eb4-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>|
|<span data-ttu-id="02eb4-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="02eb4-105">Suggestion</span></span>|<span data-ttu-id="02eb4-106">Essa alteração elimina essa dependência e permite que certificados SHA-256 sejam usados para assinar aplicativos ClickOnce destinados ao .NET Framework 4 e versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="02eb4-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>|
|<span data-ttu-id="02eb4-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="02eb4-107">Scope</span></span>|<span data-ttu-id="02eb4-108">Secundária</span><span class="sxs-lookup"><span data-stu-id="02eb4-108">Minor</span></span>|
|<span data-ttu-id="02eb4-109">Versão</span><span class="sxs-lookup"><span data-stu-id="02eb4-109">Version</span></span>|<span data-ttu-id="02eb4-110">4.6</span><span class="sxs-lookup"><span data-stu-id="02eb4-110">4.6</span></span>|
|<span data-ttu-id="02eb4-111">Type</span><span class="sxs-lookup"><span data-stu-id="02eb4-111">Type</span></span>|<span data-ttu-id="02eb4-112">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="02eb4-112">Retargeting</span></span>|
