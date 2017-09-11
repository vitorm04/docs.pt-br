---
title: "Valor de soma de verificação incorreto, dígitos não hexadecimais ou número ímpar de dígitos hexadecimais | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42033
- vbc42033
dev_langs:
- VB
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 70a8fc5e0200c15858ad1288e12b2aeb1e5303d8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="3e91b-102">Valor de soma de verificação incorreto, dígitos não hexadecimais ou número ímpar de dígitos hexadecimais</span><span class="sxs-lookup"><span data-stu-id="3e91b-102">Bad checksum value, non hex digits or odd number of hex digits</span></span>
<span data-ttu-id="3e91b-103">Um valor de soma de verificação contém dígitos hexadecimais inválidos ou um número ímpar de dígitos.</span><span class="sxs-lookup"><span data-stu-id="3e91b-103">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>  
  
 <span data-ttu-id="3e91b-104">Quando o ASP.NET gera um arquivo de origem do Visual Basic (extensão .vb), ele calcula uma soma de verificação e a coloca em um arquivo de origem oculto identificado por `#externalchecksum`.</span><span class="sxs-lookup"><span data-stu-id="3e91b-104">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="3e91b-105">Um usuário também pode gerar um arquivo .vb para isso, mas é melhor deixar esse processo para uso interno.</span><span class="sxs-lookup"><span data-stu-id="3e91b-105">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>  
  
 <span data-ttu-id="3e91b-106">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="3e91b-106">By default, this message is a warning.</span></span> <span data-ttu-id="3e91b-107">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3e91b-107">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3e91b-108">**ID do erro:** BC42033</span><span class="sxs-lookup"><span data-stu-id="3e91b-108">**Error ID:** BC42033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3e91b-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3e91b-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="3e91b-110">Se o ASP.NET estiver gerando o arquivo de origem do Visual Basic, reinicie a compilação do projeto.</span><span class="sxs-lookup"><span data-stu-id="3e91b-110">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>  
  
2.  <span data-ttu-id="3e91b-111">Se esse aviso persistir após a reinicialização, reinstale o ASP.NET e tente compilar novamente.</span><span class="sxs-lookup"><span data-stu-id="3e91b-111">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>  
  
3.  <span data-ttu-id="3e91b-112">Se o aviso ainda persistir, ou se você não estiver usando o ASP.NET, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="3e91b-112">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e91b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e91b-113">See Also</span></span>  
 <span data-ttu-id="3e91b-114">[Visão geral do ASP.NET](https://msdn.microsoft.com/library/4w3ex9c2.aspx) </span><span class="sxs-lookup"><span data-stu-id="3e91b-114">[ASP.NET Overview](https://msdn.microsoft.com/library/4w3ex9c2.aspx) </span></span>  
<span data-ttu-id="3e91b-115"> [Fale conosco](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="3e91b-115"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
