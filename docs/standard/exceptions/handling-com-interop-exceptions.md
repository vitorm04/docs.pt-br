---
title: "Manipulando exceções de interoperabilidade COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: error-reference
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc3e01bc8ca463460ede9544d1d5c095c39a59d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="f6b04-102">Manipulando exceções de interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="f6b04-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="f6b04-103">Gerenciado e o código não gerenciado pode trabalhar juntos para lidar com exceções.</span><span class="sxs-lookup"><span data-stu-id="f6b04-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="f6b04-104">Se um método lança uma exceção no código gerenciado, o common language runtime pode passar um HRESULT para um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="f6b04-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="f6b04-105">Se um método falhar no código não gerenciado retornando uma HRESULT de falha, o tempo de execução gera uma exceção que pode ser detectada pelo código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f6b04-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="f6b04-106">O tempo de execução automaticamente mapeia o HRESULT de interoperabilidade COM para exceções mais específicas.</span><span class="sxs-lookup"><span data-stu-id="f6b04-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="f6b04-107">Por exemplo, E_ACCESSDENIED se torna <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY se torna <xref:System.OutOfMemoryException>, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f6b04-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="f6b04-108">Se o HRESULT for um resultado personalizado ou for desconhecido para o tempo de execução, o tempo de execução passa um genérico <xref:System.Runtime.InteropServices.COMException> ao cliente.</span><span class="sxs-lookup"><span data-stu-id="f6b04-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="f6b04-109">O **ErrorCode** propriedade o **COMException** contém o valor HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f6b04-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="f6b04-110">Trabalhando com IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="f6b04-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="f6b04-111">Quando um erro é passado de COM para código gerenciado, o tempo de execução preenche o objeto de exceção com informações de erro.</span><span class="sxs-lookup"><span data-stu-id="f6b04-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="f6b04-112">Objetos COM que suportam IErrorInfo e retornam HRESULTS fornecem essas informações para exceções de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f6b04-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="f6b04-113">Por exemplo, o tempo de execução mapeia a descrição do erro COM a exceção <xref:System.Exception.Message%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f6b04-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="f6b04-114">Se o HRESULT não fornece nenhuma informação de erro adicional, o tempo de execução preenche muitas das propriedades da exceção com valores padrão.</span><span class="sxs-lookup"><span data-stu-id="f6b04-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="f6b04-115">Se um método falhar no código não gerenciado, uma exceção pode ser passada para um segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f6b04-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="f6b04-116">O tópico [HRESULTS e exceções](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contém uma tabela mostrando como HRESULTS mapeiam para objetos de exceção de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f6b04-116">The topic [HRESULTS and Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="f6b04-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6b04-117">See Also</span></span>
[<span data-ttu-id="f6b04-118">Exceções</span><span class="sxs-lookup"><span data-stu-id="f6b04-118">Exceptions</span></span>](index.md) 
