---
title: "Mitigação: desserialização de objetos em domínios de aplicativos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa156c914d2a1bb2ff0601d9e06c9b87d4190754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a><span data-ttu-id="d7023-102">Mitigação: desserialização de objetos em domínios de aplicativos</span><span class="sxs-lookup"><span data-stu-id="d7023-102">Mitigation: Deserialization of Objects Across App Domains</span></span>
<span data-ttu-id="d7023-103">Em alguns casos, quando um aplicativo usa dois ou mais domínios de aplicativo com bases de aplicativo diferentes, a tentativa de desserializar objetos no contexto da chamada lógica nos domínios de aplicativo aciona uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d7023-103">In some cases, when an app uses two or more app domains with different application bases, the attempt to deserialize objects in the logical call context across app domains throws an exception.</span></span>  
  
## <a name="diagnosing-the-issue"></a><span data-ttu-id="d7023-104">Diagnosticar o problema</span><span class="sxs-lookup"><span data-stu-id="d7023-104">Diagnosing the issue</span></span>  
 <span data-ttu-id="d7023-105">O problema surge na seguinte sequência de condições:</span><span class="sxs-lookup"><span data-stu-id="d7023-105">The issue arises under the following sequence of conditions:</span></span>  
  
1.  <span data-ttu-id="d7023-106">Um aplicativo usa dois ou mais domínios de aplicativo com bases de aplicativo diferentes.</span><span class="sxs-lookup"><span data-stu-id="d7023-106">An app uses two or more app domains with different application bases.</span></span>  
  
2.  <span data-ttu-id="d7023-107">Alguns tipos são adicionados explicitamente a <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> chamando-se um método como <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> ou <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d7023-107">Some types are explicitly added to the <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> by calling a method such as <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> or <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d7023-108">Esses tipos não são marcados como serializáveis e não são armazenados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="d7023-108">These types are not marked as serializable and are not stored in the global assembly cache.</span></span>  
  
3.  <span data-ttu-id="d7023-109">Mais tarde, a execução do código no domínio de aplicativo não padrão tenta ler um valor de um arquivo de configuração ou usar XML para desserializar um objeto.</span><span class="sxs-lookup"><span data-stu-id="d7023-109">Later, code running in the non-default app domain tries to read a value from a configuration file or use XML to deserialize an object.</span></span>  
  
4.  <span data-ttu-id="d7023-110">Para ler de um arquivo de configuração ou desserializar o objeto, um objeto <xref:System.Xml.XmlReader> tenta acessar o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="d7023-110">In order to read from a configuration file or deserialize the object, an <xref:System.Xml.XmlReader> object tries to access the configuration system.</span></span>  
  
5.  <span data-ttu-id="d7023-111">Se o sistema de configuração ainda não tiver sido inicializado, ele deverá concluir sua inicialização.</span><span class="sxs-lookup"><span data-stu-id="d7023-111">If the configuration system has not already been initialized, it must complete its initialization.</span></span> <span data-ttu-id="d7023-112">Isso significa, entre outras coisas, que o tempo de execução precisa criar um caminho estável para um sistema de configuração, que faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d7023-112">This means, among other things, that the runtime has to create a stable path for a configuration system, which it does as follows:</span></span>  
  
    1.  <span data-ttu-id="d7023-113">Ele procura a evidência do domínio de aplicativo não padrão.</span><span class="sxs-lookup"><span data-stu-id="d7023-113">It looks for evidence for the non-default app domain.</span></span>  
  
    2.  <span data-ttu-id="d7023-114">Ele tentar calcular a evidência para o domínio de aplicativo não padrão com base no domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="d7023-114">It tries to calculate the evidence for the non-default app domain based on the default app domain.</span></span>  
  
    3.  <span data-ttu-id="d7023-115">A chamada para obter a evidência do domínio de aplicativo padrão dispara uma chamada de domínio de aplicativo cruzado do domínio de aplicativo não padrão para o domínio de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="d7023-115">The call to get evidence for the default app domain triggers a cross-app domain call from the non-default app domain to the default app domain.</span></span>  
  
    4.  <span data-ttu-id="d7023-116">Como parte do contrato do domínio de aplicativo cruzado no .NET Framework, o conteúdo do contexto de chamada lógica também precisa de marshaling nos limites do domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7023-116">As part of the cross-app domain contract in the .NET Framework, the contents of the logical call context also have to be marshaled across app domain boundaries.</span></span>  
  
6.  <span data-ttu-id="d7023-117">Como os tipos que estão no contexto de chamada lógica não podem ser resolvidos no domínio de aplicativo padrão, uma exceção é acionada.</span><span class="sxs-lookup"><span data-stu-id="d7023-117">Because the types that are in the logical call context cannot be resolved in the default app domain, an exception is thrown.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="d7023-118">Redução</span><span class="sxs-lookup"><span data-stu-id="d7023-118">Mitigation</span></span>  
 <span data-ttu-id="d7023-119">Para resolver esse problema, faça o seguinte</span><span class="sxs-lookup"><span data-stu-id="d7023-119">To work around this issue, do the following</span></span>  
  
1.  <span data-ttu-id="d7023-120">Procure a chamada para `get_Evidence` na pilha de chamadas quando a exceção for acionada.</span><span class="sxs-lookup"><span data-stu-id="d7023-120">Look for the call to `get_Evidence` in the call stack when the exception is thrown.</span></span> <span data-ttu-id="d7023-121">A exceção pode ser qualquer uma do grande subconjunto de exceções, incluindo <xref:System.IO.FileNotFoundException> e <xref:System.Runtime.Serialization.SerializationException>.</span><span class="sxs-lookup"><span data-stu-id="d7023-121">The exception can be any of a large subset of exceptions, including <xref:System.IO.FileNotFoundException> and <xref:System.Runtime.Serialization.SerializationException>.</span></span>  
  
2.  <span data-ttu-id="d7023-122">Identifique o local no aplicativo em que nenhum objeto é adicionado ao contexto de chamada lógica e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d7023-122">Identify the place in the app where no objects are added to the logical call context and add the following code:</span></span>  
  
    ```  
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d7023-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7023-123">See Also</span></span>  
 [<span data-ttu-id="d7023-124">Alterações no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d7023-124">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)
