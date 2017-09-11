---
title: 'Como criar uma chave do Registro e definir o valor no Visual Basic:'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
dev_langs:
- VB
helpviewer_keywords:
- registry keys, creating
- registry, adding values
- registry, adding keys
- registry keys, setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
caps.latest.revision: 30
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 106a98a1b15c37eb2cac05e1a681bf7dfed3543d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="a6aa4-102">Como criar uma chave do Registro e definir o valor no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="a6aa4-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>
<span data-ttu-id="a6aa4-103">O método `CreateSubKey` do objeto `My.Computer.Registry` pode ser usado para criar uma chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="a6aa4-104">Procedimento</span><span class="sxs-lookup"><span data-stu-id="a6aa4-104">Procedure</span></span>  
  
#### <a name="to-create-a-registry-key"></a><span data-ttu-id="a6aa4-105">Criar uma chave do Registro</span><span class="sxs-lookup"><span data-stu-id="a6aa4-105">To create a registry key</span></span>  
  
-   <span data-ttu-id="a6aa4-106">Use o método `CreateSubKey` especificando em qual hive a chave será colocada, bem como o nome da chave.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="a6aa4-107">O parâmetro `Subkey` não diferencia maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="a6aa4-108">Este exemplo cria a chave do Registro `MyTestKey` em HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     <span data-ttu-id="a6aa4-109">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a6aa4-109">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span></span>  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="a6aa4-110">Criar uma chave do Registro e definir o valor</span><span class="sxs-lookup"><span data-stu-id="a6aa4-110">To create a registry key and set a value in it</span></span>  
  
1.  <span data-ttu-id="a6aa4-111">Use o método `CreateSubkey` especificando em qual hive a chave será colocada, bem como o nome da chave.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-111">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="a6aa4-112">Este exemplo cria a chave do Registro `MyTestKey` em HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-112">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     <span data-ttu-id="a6aa4-113">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a6aa4-113">[!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]</span></span>  
  
2.  <span data-ttu-id="a6aa4-114">Defina o valor com o método `SetValue`.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-114">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="a6aa4-115">Este exemplo define o valor da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-115">This example sets the string value.</span></span> <span data-ttu-id="a6aa4-116">De "MyTestKeyValue" para "Este é um valor de teste".</span><span class="sxs-lookup"><span data-stu-id="a6aa4-116">"MyTestKeyValue" to "This is a test value".</span></span>  
  
     <span data-ttu-id="a6aa4-117">[!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a6aa4-117">[!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6aa4-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6aa4-118">Example</span></span>  
 <span data-ttu-id="a6aa4-119">Este exemplo cria a chave do Registro `MyTestKey` em HKEY_CURRENT_USER e, em seguida, define o valor da cadeia de caracteres de `MyTestKeyValue` para `This is a test value`.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-119">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>  
  
 <span data-ttu-id="a6aa4-120">[!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a6aa4-120">[!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a6aa4-121">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="a6aa4-121">Robust Programming</span></span>  
 <span data-ttu-id="a6aa4-122">Analise a estrutura do Registro para encontrar um local adequado para a chave.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-122">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="a6aa4-123">Por exemplo, caso você queira abrir a chave HKEY_CURRENT_USER\Software do usuário atual e criar uma chave com o nome da empresa.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-123">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="a6aa4-124">Em seguida, adicione os valores do Registro à chave da empresa.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-124">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="a6aa4-125">Ao ler o Registro de um aplicativo Web, o usuário atual depende da autenticação e da representação implementadas no aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-125">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
 <span data-ttu-id="a6aa4-126">É mais seguro gravar dados na pasta do usuário (<xref:Microsoft.Win32.Registry.CurrentUser>) em vez de no computador local (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="a6aa4-126">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>  
  
 <span data-ttu-id="a6aa4-127">Ao criar um valor de Registro, é necessário decidir o que fazer se esse valor já existir.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-127">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="a6aa4-128">Outro processo, talvez um mal-intencionado, pode já ter criado o valor e tem acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-128">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="a6aa4-129">Ao colocar dados no valor de Registro, os dados estarão disponíveis para o outro processo.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-129">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="a6aa4-130">Para impedir isso, use o método <xref:Microsoft.Win32.RegistryKey.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-130">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="a6aa4-131">Ele retornará `Nothing` se a chave ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-131">It returns `Nothing` if the key does not already exist.</span></span>  
  
 <span data-ttu-id="a6aa4-132">Não é seguro armazenar segredos, como senhas, no Registro como texto sem formatação, mesmo se a chave do Registro estiver protegida por ACLs (Listas de Controle de Acesso).</span><span class="sxs-lookup"><span data-stu-id="a6aa4-132">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>  
  
 <span data-ttu-id="a6aa4-133">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="a6aa4-133">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="a6aa4-134">O nome da chave é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="a6aa4-134">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="a6aa4-135">O usuário não tem permissões para criar chaves do Registro (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="a6aa4-135">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="a6aa4-136">O nome da chave excede o limite de 255 caracteres (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="a6aa4-136">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="a6aa4-137">A chave é fechada (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="a6aa4-137">The key is closed (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="a6aa4-138">A chave do Registro é somente leitura (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="a6aa4-138">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a6aa4-139">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a6aa4-139">.NET Framework Security</span></span>  
 <span data-ttu-id="a6aa4-140">Para executar esse processo, seu assembly exige um nível de privilégio concedido pela classe <xref:System.Security.Permissions.RegistryPermission>.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-140">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="a6aa4-141">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-141">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="a6aa4-142">Da mesma forma, o usuário deve ter as ACLs corretas para criar ou gravar nas configurações.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-142">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="a6aa4-143">Por exemplo, um aplicativo local que tem a permissão de segurança de acesso do código pode não ter permissão do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="a6aa4-143">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="a6aa4-144">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](https://msdn.microsoft.com/library/33tceax8).</span><span class="sxs-lookup"><span data-stu-id="a6aa4-144">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6aa4-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6aa4-145">See Also</span></span>  
 <span data-ttu-id="a6aa4-146"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy></span><span class="sxs-lookup"><span data-stu-id="a6aa4-146"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy></span></span>   
 <span data-ttu-id="a6aa4-147"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A></span><span class="sxs-lookup"><span data-stu-id="a6aa4-147"><xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A></span></span>   
 <span data-ttu-id="a6aa4-148"><xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="a6aa4-148"><xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A></span></span>   
 <span data-ttu-id="a6aa4-149">[Lendo e Gravando do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="a6aa4-149">[Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span></span>  
 [<span data-ttu-id="a6aa4-150">Noções Básicas da Segurança de Acesso do Código</span><span class="sxs-lookup"><span data-stu-id="a6aa4-150">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)

