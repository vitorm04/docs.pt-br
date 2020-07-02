---
ms.openlocfilehash: c967a5b09b5e9ffeee7bff046f0c96469bc7fb02
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615589"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="ca159-101">ClickOnce é compatível com SHA-256 em aplicativos destinados ao 4.0</span><span class="sxs-lookup"><span data-stu-id="ca159-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

#### <a name="details"></a><span data-ttu-id="ca159-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ca159-102">Details</span></span>

<span data-ttu-id="ca159-103">Anteriormente, um aplicativo ClickOnce com um certificado assinado com SHA-256 exigia a presença do .NET Framework 4.5 ou posterior, mesmo se o aplicativo fosse direcionado ao 4.0.</span><span class="sxs-lookup"><span data-stu-id="ca159-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="ca159-104">Agora, os aplicativos ClickOnce direcionados ao .NET Framework 4.0 podem ser executados no .NET Framework 4.0, mesmo quando assinados com SHA-256.</span><span class="sxs-lookup"><span data-stu-id="ca159-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ca159-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ca159-105">Suggestion</span></span>

<span data-ttu-id="ca159-106">Essa alteração elimina essa dependência e permite que certificados SHA-256 sejam usados para assinar aplicativos ClickOnce destinados ao .NET Framework 4 e versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="ca159-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>

| <span data-ttu-id="ca159-107">Name</span><span class="sxs-lookup"><span data-stu-id="ca159-107">Name</span></span>    | <span data-ttu-id="ca159-108">Valor</span><span class="sxs-lookup"><span data-stu-id="ca159-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ca159-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="ca159-109">Scope</span></span>   | <span data-ttu-id="ca159-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="ca159-110">Minor</span></span>       |
| <span data-ttu-id="ca159-111">Versão</span><span class="sxs-lookup"><span data-stu-id="ca159-111">Version</span></span> | <span data-ttu-id="ca159-112">4.6</span><span class="sxs-lookup"><span data-stu-id="ca159-112">4.6</span></span>         |
| <span data-ttu-id="ca159-113">Type</span><span class="sxs-lookup"><span data-stu-id="ca159-113">Type</span></span>    | <span data-ttu-id="ca159-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ca159-114">Retargeting</span></span> |
