---
title: Como criar uma chave do Registro e definir o valor
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 459c4b3f971009ee4b6b669c55bc058db0826595
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349197"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="54f40-102">Como criar uma chave do Registro e definir o valor no Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="54f40-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="54f40-103">O método `CreateSubKey` do objeto `My.Computer.Registry` pode ser usado para criar uma chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="54f40-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="54f40-104">Procedimento</span><span class="sxs-lookup"><span data-stu-id="54f40-104">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="54f40-105">Criar uma chave do Registro</span><span class="sxs-lookup"><span data-stu-id="54f40-105">To create a registry key</span></span>

- <span data-ttu-id="54f40-106">Use o método `CreateSubKey` especificando em qual hive a chave será colocada, bem como o nome da chave.</span><span class="sxs-lookup"><span data-stu-id="54f40-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="54f40-107">O parâmetro `Subkey` não diferencia maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="54f40-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="54f40-108">Este exemplo cria a chave do Registro `MyTestKey` em HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="54f40-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="54f40-109">Criar uma chave do Registro e definir o valor</span><span class="sxs-lookup"><span data-stu-id="54f40-109">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="54f40-110">Use o método `CreateSubkey` especificando em qual hive a chave será colocada, bem como o nome da chave.</span><span class="sxs-lookup"><span data-stu-id="54f40-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="54f40-111">Este exemplo cria a chave do Registro `MyTestKey` em HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="54f40-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="54f40-112">Defina o valor com o método `SetValue`.</span><span class="sxs-lookup"><span data-stu-id="54f40-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="54f40-113">Este exemplo define o valor da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="54f40-113">This example sets the string value.</span></span> <span data-ttu-id="54f40-114">De "MyTestKeyValue" para "Este é um valor de teste".</span><span class="sxs-lookup"><span data-stu-id="54f40-114">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="54f40-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54f40-115">Example</span></span>

<span data-ttu-id="54f40-116">Este exemplo cria a chave do Registro `MyTestKey` em HKEY_CURRENT_USER e, em seguida, define o valor da cadeia de caracteres de `MyTestKeyValue` para `This is a test value`.</span><span class="sxs-lookup"><span data-stu-id="54f40-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="54f40-117">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="54f40-117">Robust Programming</span></span>

<span data-ttu-id="54f40-118">Analise a estrutura do Registro para encontrar um local adequado para a chave.</span><span class="sxs-lookup"><span data-stu-id="54f40-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="54f40-119">Por exemplo, caso você queira abrir a chave HKEY_CURRENT_USER\Software do usuário atual e criar uma chave com o nome da empresa.</span><span class="sxs-lookup"><span data-stu-id="54f40-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="54f40-120">Em seguida, adicione os valores do Registro à chave da empresa.</span><span class="sxs-lookup"><span data-stu-id="54f40-120">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="54f40-121">Ao ler o Registro de um aplicativo Web, o usuário atual depende da autenticação e da representação implementadas no aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="54f40-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="54f40-122">É mais seguro gravar dados na pasta do usuário (<xref:Microsoft.Win32.Registry.CurrentUser>) em vez de no computador local (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="54f40-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="54f40-123">Ao criar um valor de Registro, é necessário decidir o que fazer se esse valor já existir.</span><span class="sxs-lookup"><span data-stu-id="54f40-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="54f40-124">Outro processo, talvez um mal-intencionado, pode já ter criado o valor e tem acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="54f40-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="54f40-125">Ao colocar dados no valor de Registro, os dados estarão disponíveis para o outro processo.</span><span class="sxs-lookup"><span data-stu-id="54f40-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="54f40-126">Para impedir isso, use o método <xref:Microsoft.Win32.RegistryKey.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="54f40-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="54f40-127">Ele retornará `Nothing` se a chave ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="54f40-127">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="54f40-128">Não é seguro armazenar segredos, como senhas, no Registro como texto sem formatação, mesmo se a chave do Registro estiver protegida por ACLs (Listas de Controle de Acesso).</span><span class="sxs-lookup"><span data-stu-id="54f40-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="54f40-129">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="54f40-129">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="54f40-130">O nome da chave é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="54f40-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="54f40-131">O usuário não tem permissões para criar chaves do Registro (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="54f40-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="54f40-132">O nome da chave excede o limite de 255 caracteres (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="54f40-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="54f40-133">A chave é fechada (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="54f40-133">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="54f40-134">A chave do Registro é somente leitura (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="54f40-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="54f40-135">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="54f40-135">.NET Framework Security</span></span>

<span data-ttu-id="54f40-136">Para executar esse processo, seu assembly exige um nível de privilégio concedido pela classe <xref:System.Security.Permissions.RegistryPermission>.</span><span class="sxs-lookup"><span data-stu-id="54f40-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="54f40-137">Se você estiver executando em um contexto de confiança parcial, o processo poderá gerar uma exceção em razão dos privilégios insuficientes.</span><span class="sxs-lookup"><span data-stu-id="54f40-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="54f40-138">Da mesma forma, o usuário deve ter as ACLs corretas para criar ou gravar nas configurações.</span><span class="sxs-lookup"><span data-stu-id="54f40-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="54f40-139">Por exemplo, um aplicativo local que tem a permissão de segurança de acesso do código pode não ter permissão do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="54f40-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="54f40-140">Para obter mais informações, consulte [Noções Básicas da Segurança de Acesso do Código](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="54f40-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54f40-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54f40-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="54f40-142">Lendo e Gravando do Registro</span><span class="sxs-lookup"><span data-stu-id="54f40-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="54f40-143">Noções Básicas da Segurança de Acesso do Código</span><span class="sxs-lookup"><span data-stu-id="54f40-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
