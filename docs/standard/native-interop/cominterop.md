---
title: Interoperabilidade COM no .NET
description: Saiba como executar a interoperação com bibliotecas COM no .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 07/11/2019
ms.openlocfilehash: 03ede2fc95f4114a4d80423bd7de2e46012a2431
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631420"
---
# <a name="com-interop-in-net"></a><span data-ttu-id="6bd2e-103">Interoperabilidade COM no .NET</span><span class="sxs-lookup"><span data-stu-id="6bd2e-103">COM Interop in .NET</span></span>

<span data-ttu-id="6bd2e-104">O COM (Component Object Model) permite que um objeto exponha sua funcionalidade a outros componentes e aplicativos host em plataformas Windows.</span><span class="sxs-lookup"><span data-stu-id="6bd2e-104">The Component Object Model (COM) lets an object expose its functionality to other components and to host applications on Windows platforms.</span></span> <span data-ttu-id="6bd2e-105">Para ajudar a permitir que os usuários executem a interoperação com as bases de código existentes, o .NET Framework sempre forneceu um forte suporte para interoperação com bibliotecas COM.</span><span class="sxs-lookup"><span data-stu-id="6bd2e-105">To help enable users to interoperate with their existing code bases, the .NET Framework has always provided strong support for interoperating with COM libraries.</span></span> <span data-ttu-id="6bd2e-106">No .NET Core 3.0, uma grande parte desse suporte foi adicionada ao .NET Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="6bd2e-106">In .NET Core 3.0, a large portion of this support has been added to .NET Core on Windows.</span></span> <span data-ttu-id="6bd2e-107">Esta documentação explicará como as tecnologias comuns de interoperabilidade COM funcionam e como você pode utilizá-las para executar a interoperação com as bibliotecas COM existentes.</span><span class="sxs-lookup"><span data-stu-id="6bd2e-107">The documentation here will explain how the common COM interop techonologies work and how you can utilize them to interoperate with your existing COM libraries.</span></span>

- [<span data-ttu-id="6bd2e-108">Wrappers COM)</span><span class="sxs-lookup"><span data-stu-id="6bd2e-108">COM Wrappers)</span></span>](./com-wrappers.md)
- [<span data-ttu-id="6bd2e-109">COM Callable Wrappers</span><span class="sxs-lookup"><span data-stu-id="6bd2e-109">COM Callable Wrappers</span></span>](./com-callable-wrapper.md)
- [<span data-ttu-id="6bd2e-110">RCWs (Runtime Callable Wrappers)</span><span class="sxs-lookup"><span data-stu-id="6bd2e-110">Runtime Callable Wrappers</span></span>](./runtime-callable-wrapper.md)
- [<span data-ttu-id="6bd2e-111">Tipos .NET qualificados para interoperação COM</span><span class="sxs-lookup"><span data-stu-id="6bd2e-111">Qualifying .NET Types for COM Interoperation</span></span>](./qualify-net-types-for-interoperation.md)
