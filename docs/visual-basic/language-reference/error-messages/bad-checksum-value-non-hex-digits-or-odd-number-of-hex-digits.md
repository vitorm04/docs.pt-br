---
title: Valor de soma de verificação incorreto, dígitos não hexadecimais ou número ímpar de dígitos hexadecimais
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 1ae4113505ca63df9b20e6e71aa0b418da4ef924
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197354"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="6202e-102">Valor de soma de verificação incorreto, dígitos não hexadecimais ou número ímpar de dígitos hexadecimais</span><span class="sxs-lookup"><span data-stu-id="6202e-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>
<span data-ttu-id="6202e-103">Um valor de soma de verificação contém dígitos hexadecimais inválidos ou um número ímpar de dígitos.</span><span class="sxs-lookup"><span data-stu-id="6202e-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="6202e-104">Quando o ASP.NET gera um arquivo de origem do Visual Basic (extensão .vb), ele calcula uma soma de verificação e a coloca em um arquivo de origem oculto identificado por `#externalchecksum`.</span><span class="sxs-lookup"><span data-stu-id="6202e-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="6202e-105">Um usuário também pode gerar um arquivo .vb para isso, mas é melhor deixar esse processo para uso interno.</span><span class="sxs-lookup"><span data-stu-id="6202e-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="6202e-106">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="6202e-106">By default, this message is a warning.</span></span> <span data-ttu-id="6202e-107">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6202e-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6202e-108">**ID do erro:** BC42033</span><span class="sxs-lookup"><span data-stu-id="6202e-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6202e-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6202e-109">To correct this error</span></span>  
  
1. <span data-ttu-id="6202e-110">Se o ASP.NET estiver gerando o arquivo de origem do Visual Basic, reinicie a compilação do projeto.</span><span class="sxs-lookup"><span data-stu-id="6202e-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2. <span data-ttu-id="6202e-111">Se esse aviso persistir após a reinicialização, reinstale o ASP.NET e tente compilar novamente.</span><span class="sxs-lookup"><span data-stu-id="6202e-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3. <span data-ttu-id="6202e-112">Se o aviso ainda persistir, ou se você não estiver usando o ASP.NET, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="6202e-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6202e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6202e-113">See also</span></span>

- [<span data-ttu-id="6202e-114">Visão geral do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6202e-114">ASP.NET Overview</span></span>](/aspnet/overview)
- [<span data-ttu-id="6202e-115">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="6202e-115">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
