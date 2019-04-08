---
title: Segurança e Registro (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: dc0071d1fddf99bd712ebe8aea5c61bbc3522f93
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839347"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="8ecfc-102">Segurança e Registro (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ecfc-102">Security and the Registry (Visual Basic)</span></span>
<span data-ttu-id="8ecfc-103">Esta página discute as implicações de segurança de armazenar dados no Registro.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="8ecfc-104">Permissões</span><span class="sxs-lookup"><span data-stu-id="8ecfc-104">Permissions</span></span>  
 <span data-ttu-id="8ecfc-105">Não é seguro armazenar segredos, como senhas, no Registro como texto sem formatação, mesmo se a chave do Registro estiver protegida por ACLs (listas de controle de acesso).</span><span class="sxs-lookup"><span data-stu-id="8ecfc-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="8ecfc-106">Trabalhar com o Registro pode comprometer a segurança ao permitir o acesso inadequado aos recursos do sistema ou a informações protegidas.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="8ecfc-107">Para usar essas propriedades, é necessário ter lido e gravado permissões da enumeração <xref:System.Security.Permissions.RegistryPermissionAccess>, que controla o acesso a variáveis do Registro.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="8ecfc-108">Qualquer código sendo executado com confiança total (nos termos da política de segurança padrão, é qualquer código instalado no disco rígido local do usuário) tem as permissões necessárias para acessar o Registro.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="8ecfc-109">Para saber mais, confira a classe <xref:System.Security.Permissions.RegistryPermission>.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="8ecfc-110">As variáveis de Registro não devem ser armazenadas em locais de memória em que o código sem <xref:System.Security.Permissions.RegistryPermission> possa acessá-los.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="8ecfc-111">Da mesma forma, ao conceder permissões, conceda os privilégios mínimos necessários para realizar o trabalho.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="8ecfc-112">Os valores de acesso de permissão ao Registro são definidos pela enumeração <xref:System.Security.Permissions.RegistryPermissionAccess>.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="8ecfc-113">A tabela a seguir detalha seus membros.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="8ecfc-114">Valor</span><span class="sxs-lookup"><span data-stu-id="8ecfc-114">Value</span></span>|<span data-ttu-id="8ecfc-115">Acesso às variáveis de Registro</span><span class="sxs-lookup"><span data-stu-id="8ecfc-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="8ecfc-116">Criar, ler e gravar</span><span class="sxs-lookup"><span data-stu-id="8ecfc-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="8ecfc-117">Create</span><span class="sxs-lookup"><span data-stu-id="8ecfc-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="8ecfc-118">Sem acesso</span><span class="sxs-lookup"><span data-stu-id="8ecfc-118">No access</span></span>|  
|`Read`|<span data-ttu-id="8ecfc-119">Ler</span><span class="sxs-lookup"><span data-stu-id="8ecfc-119">Read</span></span>|  
|`Write`|<span data-ttu-id="8ecfc-120">Write</span><span class="sxs-lookup"><span data-stu-id="8ecfc-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="8ecfc-121">Verificando valores nas chaves do Registro</span><span class="sxs-lookup"><span data-stu-id="8ecfc-121">Checking Values in Registry Keys</span></span>  
 <span data-ttu-id="8ecfc-122">Ao criar um valor de Registro, é necessário decidir o que fazer se esse valor já existir.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="8ecfc-123">Outro processo, talvez um mal-intencionado, pode já ter criado o valor e tem acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="8ecfc-124">Ao colocar dados no valor de Registro, os dados estarão disponíveis para o outro processo.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="8ecfc-125">Para impedir isso, use o método `GetValue`.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="8ecfc-126">Ele retornará `Nothing` se a chave ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ecfc-127">Ao ler o Registro em um aplicativo Web, a identidade do usuário atual depende da autenticação e da representação implementadas no aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="8ecfc-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecfc-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ecfc-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="8ecfc-129">Lendo e Gravando do Registro</span><span class="sxs-lookup"><span data-stu-id="8ecfc-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
