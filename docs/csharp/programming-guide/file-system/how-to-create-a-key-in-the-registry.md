---
title: Como criar uma chave no Registro (Visual C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: 96d34df3314494fc96ad8b55d7462b67dcc7bd72
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a><span data-ttu-id="54e40-102">Como criar uma chave no Registro (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="54e40-102">How to: Create a Key In the Registry (Visual C#)</span></span>
<span data-ttu-id="54e40-103">Este exemplo adiciona o par de valores, "Name" e "Isabella", ao Registro do usuário atual, sob a chave "Names".</span><span class="sxs-lookup"><span data-stu-id="54e40-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="54e40-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54e40-104">Example</span></span>  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="54e40-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="54e40-105">Compiling the Code</span></span>  
  
-   <span data-ttu-id="54e40-106">Copie o código e cole-o no método `Main` de um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="54e40-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
-   <span data-ttu-id="54e40-107">Substitua o parâmetro `Names` pelo nome de uma chave existente diretamente sob o nó HKEY_CURRENT_USER do Registro.</span><span class="sxs-lookup"><span data-stu-id="54e40-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
-   <span data-ttu-id="54e40-108">Substitua o parâmetro `Name` pelo nome de um valor que existe diretamente sob o nó Names.</span><span class="sxs-lookup"><span data-stu-id="54e40-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="54e40-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="54e40-109">Robust Programming</span></span>  
 <span data-ttu-id="54e40-110">Analise a estrutura do Registro para encontrar um local adequado para a chave.</span><span class="sxs-lookup"><span data-stu-id="54e40-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="54e40-111">Por exemplo, caso você queira abrir a chave Software do usuário atual e criar uma chave com o nome da empresa.</span><span class="sxs-lookup"><span data-stu-id="54e40-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="54e40-112">Em seguida, adicione os valores do Registro à chave da empresa.</span><span class="sxs-lookup"><span data-stu-id="54e40-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="54e40-113">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="54e40-113">The following conditions might cause an exception:</span></span>  
  
-   <span data-ttu-id="54e40-114">O nome da chave é nulo.</span><span class="sxs-lookup"><span data-stu-id="54e40-114">The name of the key is null.</span></span>  
  
-   <span data-ttu-id="54e40-115">O usuário não tem permissões para criar chaves do Registro.</span><span class="sxs-lookup"><span data-stu-id="54e40-115">The user does not have permissions to create registry keys.</span></span>  
  
-   <span data-ttu-id="54e40-116">O nome da chave excede o limite de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="54e40-116">The key name exceeds the 255-character limit.</span></span>  
  
-   <span data-ttu-id="54e40-117">A chave é fechada.</span><span class="sxs-lookup"><span data-stu-id="54e40-117">The key is closed.</span></span>  
  
-   <span data-ttu-id="54e40-118">A chave do Registro é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="54e40-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="54e40-119">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="54e40-119">.NET Framework Security</span></span>  
 <span data-ttu-id="54e40-120">É mais seguro gravar dados na pasta do usuário — `Microsoft.Win32.Registry.CurrentUser` — em vez de no computador local — `Microsoft.Win32.Registry.LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="54e40-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="54e40-121">Ao criar um valor de Registro, é necessário decidir o que fazer se esse valor já existir.</span><span class="sxs-lookup"><span data-stu-id="54e40-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="54e40-122">Outro processo, talvez um mal-intencionado, pode já ter criado o valor e tem acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="54e40-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="54e40-123">Ao colocar dados no valor de Registro, os dados estarão disponíveis para o outro processo.</span><span class="sxs-lookup"><span data-stu-id="54e40-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="54e40-124">Para impedir isso, use o método `Overload:Microsoft.Win32.RegistryKey.GetValue`.</span><span class="sxs-lookup"><span data-stu-id="54e40-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="54e40-125">ProcessOnStatus...</span><span class="sxs-lookup"><span data-stu-id="54e40-125">method.</span></span> <span data-ttu-id="54e40-126">Ele retornará null se a chave ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="54e40-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="54e40-127">Não é seguro armazenar segredos, como senhas, no Registro como texto sem formatação, mesmo se a chave do Registro estiver protegida por ACL (listas de controle de acesso).</span><span class="sxs-lookup"><span data-stu-id="54e40-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e40-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54e40-128">See Also</span></span>  
 <span data-ttu-id="54e40-129"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="54e40-129"><xref:System.IO?displayProperty=fullName></span></span>   
 <span data-ttu-id="54e40-130">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="54e40-130">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="54e40-131">[Sistema de arquivos e o Registro (Guia de Programação em C#)](../../../csharp/programming-guide/file-system/index.md) </span><span class="sxs-lookup"><span data-stu-id="54e40-131">[File System and the Registry (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md) </span></span>  
 [<span data-ttu-id="54e40-132">Ler, gravar e excluir do Registro com C#</span><span class="sxs-lookup"><span data-stu-id="54e40-132">Read, write and delete from the registry with C#</span></span>](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)

