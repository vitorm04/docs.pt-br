---
title: "Como detectar a disponibilidade de rede e alterações de endereço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
caps.latest.revision: 4
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 52c3bffb204c35d7741d7e4fb35b05a357f3811f
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="69bdd-102">Como detectar a disponibilidade de rede e alterações de endereço</span><span class="sxs-lookup"><span data-stu-id="69bdd-102">How to: Detect Network Availability and Address Changes</span></span>
<span data-ttu-id="69bdd-103">Este exemplo mostra como detectar alterações no endereço de rede de uma interface.</span><span class="sxs-lookup"><span data-stu-id="69bdd-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69bdd-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69bdd-104">Example</span></span>  
  
```  
using System;  
using System.Net;  
using System.Net.NetworkInformation;  
  
namespace Examples.Net.AddressChanges  
{  
    public class NetworkingExample  
    {  
        public static void Main()  
        {  
            NetworkChange.NetworkAddressChanged += new   
             NetworkAddressChangedEventHandler(AddressChangedCallback);  
            Console.WriteLine("Listening for address changes. Press any key to exit.");  
            Console.ReadLine();  
        }  
        static void AddressChangedCallback(object sender, EventArgs e)  
        {  
  
            NetworkInterface[] adapters = NetworkInterface.GetAllNetworkInterfaces();  
            foreach(NetworkInterface n in adapters)  
            {  
                Console.WriteLine("   {0} is {1}", n.Name, n.OperationalStatus);  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="69bdd-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="69bdd-105">Compiling the Code</span></span>  
 <span data-ttu-id="69bdd-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="69bdd-106">This example requires:</span></span>  
  
-   <span data-ttu-id="69bdd-107">Referências ao namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="69bdd-107">References to the **System.Net** namespace.</span></span>

