---
title: Como ler um valor a partir de uma chave do Registro no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f88401f6daa7a2108522496c845521474c22cc30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="8c2aa-102">Como ler um valor a partir de uma chave do Registro no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c2aa-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>
<span data-ttu-id="8c2aa-103">O método `GetValue` do objeto `My.Computer.Registry` pode ser usado para ler valores no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="8c2aa-104">Se a chave, "Software\MyApp" no exemplo a seguir, não existir, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="8c2aa-105">Se o `ValueName`, "Name" no exemplo a seguir, não existir, `Nothing` será retornado.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="8c2aa-106">O método `GetValue` também pode ser usado para determinar se um determinado valor existe em uma chave do Registro específica.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="8c2aa-107">Quando o código lê o Registro de um aplicativo Web, o usuário atual será determinado pela autenticação e a representação implementadas no aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="8c2aa-108">Para ler um valor de uma chave do Registro</span><span class="sxs-lookup"><span data-stu-id="8c2aa-108">To read a value from a registry key</span></span>  
  
-   <span data-ttu-id="8c2aa-109">Use o método `GetValue` (especificando o caminho e nome) para ler um valor de chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="8c2aa-110">O exemplo a seguir lê o valor `Name` de `HKEY_CURRENT_USER\Software\MyApp` e o exibe em uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 <span data-ttu-id="8c2aa-111">Este exemplo de código também está disponível como um trecho de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="8c2aa-112">No seletor de trecho de código, ele está localizado em **Sistema Operacional Windows > Registro**.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="8c2aa-113">Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="8c2aa-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="8c2aa-114">Para determinar se um valor existe em uma chave do Registro</span><span class="sxs-lookup"><span data-stu-id="8c2aa-114">To determine whether a value exists in a registry key</span></span>  
  
-   <span data-ttu-id="8c2aa-115">Use o método `GetValue` para recuperar o valor.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="8c2aa-116">O código a seguir verifica se o valor existe e retorna uma mensagem se ele não existir.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8c2aa-117">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="8c2aa-117">Robust Programming</span></span>  
 <span data-ttu-id="8c2aa-118">O Registro contém chaves de nível superior ou raiz, que são usadas para armazenar dados.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="8c2aa-119">Por exemplo, a chave raiz HKEY_LOCAL_MACHINE é usada para armazenar configurações de nível do computador usadas por todos os usuários, enquanto HKEY_CURRENT_USER é usada para armazenar dados específicos a um usuário individual.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="8c2aa-120">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="8c2aa-120">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="8c2aa-121">O nome da chave é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="8c2aa-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="8c2aa-122">O usuário não tem permissões para ler nas chaves do Registro (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="8c2aa-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="8c2aa-123">O nome da chave excede o limite de 255 caracteres (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="8c2aa-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8c2aa-124">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8c2aa-124">.NET Framework Security</span></span>  
 <span data-ttu-id="8c2aa-125">Para executar esse processo, seu assembly exige um nível de privilégio concedido pela classe <xref:System.Security.Permissions.RegistryPermission>.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="8c2aa-126">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="8c2aa-127">Da mesma forma, o usuário deve ter as ACLs corretas para criar ou gravar nas configurações.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="8c2aa-128">Por exemplo, um aplicativo local que tem a permissão de segurança de acesso do código pode não ter permissão do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="8c2aa-129">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](https://msdn.microsoft.com/library/33tceax8).</span><span class="sxs-lookup"><span data-stu-id="8c2aa-129">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c2aa-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c2aa-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.Win32.RegistryHive>  
 [<span data-ttu-id="8c2aa-131">Lendo e Gravando do Registro</span><span class="sxs-lookup"><span data-stu-id="8c2aa-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
