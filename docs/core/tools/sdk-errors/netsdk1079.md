---
title: 'NETSDK1079: o pacote Microsoft. AspNetCore. All não tem suporte ao direcionar o .NET Core 3,0 ou superior.'
description: Como resolver a migração para fora do Microsoft. AspNetCore. app
author: dsplaisted
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1079
ms.openlocfilehash: e0b7aba909dbd2931f755238a2de2418d294751d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445743"
---
# <a name="netsdk1079-the-microsoftaspnetcoreall-package-is-not-supported-when-targeting-net-core-30-or-higher"></a><span data-ttu-id="8914d-103">NETSDK1079: o pacote Microsoft. AspNetCore. All não tem suporte ao direcionar o .NET Core 3,0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="8914d-103">NETSDK1079: The Microsoft.AspNetCore.All package is not supported when targeting .NET Core 3.0 or higher.</span></span>

<span data-ttu-id="8914d-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 3.1.100 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="8914d-104">**This article applies to:** ✔️ .NET Core SDK 3.1.100 and later versions</span></span>

<span data-ttu-id="8914d-105">Você pode receber essa mensagem de erro quando:</span><span class="sxs-lookup"><span data-stu-id="8914d-105">You may receive this error message when:</span></span>

- <span data-ttu-id="8914d-106">Redirecione um projeto ASP.NET Core do .NET Core 2,2 ou anterior para o .NET Core 3,0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="8914d-106">You retarget an ASP.NET Core project from .NET Core 2.2 or earlier to .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="8914d-107">O projeto usa o pacote Microsoft. AspNetCore. All.</span><span class="sxs-lookup"><span data-stu-id="8914d-107">The project uses the Microsoft.AspNetCore.All package.</span></span>

<span data-ttu-id="8914d-108">Remova o `PackageReference` para Microsoft. AspNetCore. All.</span><span class="sxs-lookup"><span data-stu-id="8914d-108">Remove the `PackageReference` for Microsoft.AspNetCore.All.</span></span>  <span data-ttu-id="8914d-109">Talvez você também precise adicionar referências de pacote para pacotes que foram referenciados de Microsoft. AspNetCore. All, mas não estão incluídos na estrutura compartilhada ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8914d-109">You may also need to add package references for packages that were referenced from Microsoft.AspNetCore.All but are not included in the ASP.NET Core shared framework.</span></span>  <span data-ttu-id="8914d-110">Esses pacotes estão listados aqui: [migrando do Microsoft. AspNetCore. All para Microsoft. AspNetCore. app](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp).</span><span class="sxs-lookup"><span data-stu-id="8914d-110">These packages are listed here: [Migrating from Microsoft.AspNetCore.All to Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp).</span></span>

<span data-ttu-id="8914d-111">Consulte também [migrar de ASP.NET Core 2,2 para 3,0](/aspnet/core/migration/22-to-30)</span><span class="sxs-lookup"><span data-stu-id="8914d-111">See also [Migrate from ASP.NET Core 2.2 to 3.0](/aspnet/core/migration/22-to-30)</span></span>
