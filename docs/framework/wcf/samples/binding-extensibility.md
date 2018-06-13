---
title: Extensibilidade de associação
ms.date: 03/30/2017
ms.assetid: cabdd583-ddf5-493e-9dba-c6c31cde8f65
ms.openlocfilehash: af9736a1011c3de6e1add51e8a913745cfd6756d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498968"
---
# <a name="binding-extensibility"></a><span data-ttu-id="6d614-102">Extensibilidade de associação</span><span class="sxs-lookup"><span data-stu-id="6d614-102">Binding Extensibility</span></span>

<span data-ttu-id="6d614-103">Esta seção contém exemplos que demonstram a associação personalizada no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6d614-103">This section contains samples that demonstrate custom binding in Windows Communication Foundation (WCF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d614-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6d614-104">In This Section</span></span>  
 <xref:System.ServiceModel.NetHttpBinding>  
 <span data-ttu-id="6d614-105">Demonstra como implementar uma associação que empilha <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ou <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> sobre o <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="6d614-105">Demonstrates how to implement a binding that stacks <xref:System.ServiceModel.Channels.HttpTransportBindingElement> or the <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> on top of the <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.</span></span>  
  
 [<span data-ttu-id="6d614-106">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6d614-106">WSStreamedHttpBinding</span></span>](wsstreamedhttpbinding.md)  
 <span data-ttu-id="6d614-107">Demonstra como criar uma associação que foi projetada para oferecer suporte a cenários de streaming quando o transporte HTTP é usado.</span><span class="sxs-lookup"><span data-stu-id="6d614-107">Demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>  
