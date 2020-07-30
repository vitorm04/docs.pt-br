---
title: Como criar uma chave no registro-guia de programação C#
description: Saiba como criar uma chave no registro. Consulte um exemplo de código, compilando instruções e recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 6db076bc22e098c285b74a8c10e8b5f456c2c55e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299975"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a><span data-ttu-id="c23ad-104">Como criar uma chave no registro (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="c23ad-104">How to create a key in the registry (C# Programming Guide)</span></span>
<span data-ttu-id="c23ad-105">Este exemplo adiciona o par de valores, "Name" e "Isabella", ao Registro do usuário atual, sob a chave "Names".</span><span class="sxs-lookup"><span data-stu-id="c23ad-105">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="c23ad-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c23ad-106">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c23ad-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c23ad-107">Compiling the Code</span></span>  
  
- <span data-ttu-id="c23ad-108">Copie o código e cole-o no método `Main` de um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="c23ad-108">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="c23ad-109">Substitua o parâmetro `Names` pelo nome de uma chave existente diretamente sob o nó HKEY_CURRENT_USER do Registro.</span><span class="sxs-lookup"><span data-stu-id="c23ad-109">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="c23ad-110">Substitua o parâmetro `Name` pelo nome de um valor que existe diretamente sob o nó Names.</span><span class="sxs-lookup"><span data-stu-id="c23ad-110">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c23ad-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="c23ad-111">Robust Programming</span></span>  
 <span data-ttu-id="c23ad-112">Analise a estrutura do Registro para encontrar um local adequado para a chave.</span><span class="sxs-lookup"><span data-stu-id="c23ad-112">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="c23ad-113">Por exemplo, caso você queira abrir a chave Software do usuário atual e criar uma chave com o nome da empresa.</span><span class="sxs-lookup"><span data-stu-id="c23ad-113">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="c23ad-114">Em seguida, adicione os valores do Registro à chave da empresa.</span><span class="sxs-lookup"><span data-stu-id="c23ad-114">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="c23ad-115">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="c23ad-115">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="c23ad-116">O nome da chave é nulo.</span><span class="sxs-lookup"><span data-stu-id="c23ad-116">The name of the key is null.</span></span>  
  
- <span data-ttu-id="c23ad-117">O usuário não tem permissões para criar chaves do Registro.</span><span class="sxs-lookup"><span data-stu-id="c23ad-117">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="c23ad-118">O nome da chave excede o limite de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="c23ad-118">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="c23ad-119">A chave é fechada.</span><span class="sxs-lookup"><span data-stu-id="c23ad-119">The key is closed.</span></span>  
  
- <span data-ttu-id="c23ad-120">A chave do Registro é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="c23ad-120">The registry key is read-only.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="c23ad-121">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="c23ad-121">.NET Security</span></span>  
 <span data-ttu-id="c23ad-122">É mais seguro gravar dados na pasta do usuário — `Microsoft.Win32.Registry.CurrentUser` — em vez de no computador local — `Microsoft.Win32.Registry.LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="c23ad-122">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="c23ad-123">Ao criar um valor de Registro, é necessário decidir o que fazer se esse valor já existir.</span><span class="sxs-lookup"><span data-stu-id="c23ad-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="c23ad-124">Outro processo, talvez um mal-intencionado, pode já ter criado o valor e tem acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="c23ad-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="c23ad-125">Ao colocar dados no valor de Registro, os dados estarão disponíveis para o outro processo.</span><span class="sxs-lookup"><span data-stu-id="c23ad-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="c23ad-126">Para impedir isso, use o método `Overload:Microsoft.Win32.RegistryKey.GetValue`.</span><span class="sxs-lookup"><span data-stu-id="c23ad-126">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="c23ad-127">método.</span><span class="sxs-lookup"><span data-stu-id="c23ad-127">method.</span></span> <span data-ttu-id="c23ad-128">Ele retornará null se a chave ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="c23ad-128">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="c23ad-129">Não é seguro armazenar segredos, como senhas, no Registro como texto sem formatação, mesmo se a chave do Registro estiver protegida por ACL (listas de controle de acesso).</span><span class="sxs-lookup"><span data-stu-id="c23ad-129">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c23ad-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="c23ad-130">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="c23ad-131">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="c23ad-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c23ad-132">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c23ad-132">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="c23ad-133">Ler, gravar e excluir do Registro com C#</span><span class="sxs-lookup"><span data-stu-id="c23ad-133">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
