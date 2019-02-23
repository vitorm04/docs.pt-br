---
title: Segurança do Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: 1da8e2c6ed8091b5931e8b0a881b54329228e82a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746779"
---
# <a name="windows-forms-security"></a><span data-ttu-id="e67cd-102">Segurança do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e67cd-102">Windows Forms Security</span></span>
<span data-ttu-id="e67cd-103">O Windows Forms oferece um modelo de segurança baseado em código (os níveis de segurança são definidos para o código, independentemente do usuário que o executa).</span><span class="sxs-lookup"><span data-stu-id="e67cd-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="e67cd-104">Isso vai além de qualquer esquema de segurança que já pode estar em vigor no seu sistema de computador.</span><span class="sxs-lookup"><span data-stu-id="e67cd-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="e67cd-105">Eles podem incluir os do navegador (como a segurança baseada em zonas disponível no Internet Explorer) ou do sistema operacional (como a segurança baseada em credenciais do Windows NT).</span><span class="sxs-lookup"><span data-stu-id="e67cd-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e67cd-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e67cd-106">In This Section</span></span>  
 [<span data-ttu-id="e67cd-107">Visão geral da segurança dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e67cd-107">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 <span data-ttu-id="e67cd-108">Explica brevemente o modelo de segurança do .NET Framework e as etapas básicas necessárias para garantir que o Windows Forms no seu aplicativo esteja seguro.</span><span class="sxs-lookup"><span data-stu-id="e67cd-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="e67cd-109">Acesso mais seguro a arquivos e a dados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e67cd-109">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="e67cd-110">Descreve como acessar arquivos e dados em um ambiente de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="e67cd-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="e67cd-111">Impressão mais segura nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e67cd-111">More Secure Printing in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="e67cd-112">Descreve como acessar recursos de impressão em um ambiente de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="e67cd-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="e67cd-113">Considerações adicionais sobre segurança nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e67cd-113">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="e67cd-114">Descreve como realizar manipulação de janela, como usar a Área de Transferência e como fazer chamadas a código não gerenciado em um ambiente de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="e67cd-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e67cd-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e67cd-115">Related Sections</span></span>  
 <span data-ttu-id="e67cd-116">[Política de segurança padrão](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e67cd-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="e67cd-117">Lista as permissões padrão concedidas nos conjuntos de permissão de Confiança Total, Intranet Local e Internet.</span><span class="sxs-lookup"><span data-stu-id="e67cd-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="e67cd-118">[Administração de política de segurança geral](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e67cd-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="e67cd-119">Fornece informações sobre como administrar a política de segurança do .NET Framework e elevar as permissões.</span><span class="sxs-lookup"><span data-stu-id="e67cd-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="e67cd-120">Permissões perigosas e administração de política</span><span class="sxs-lookup"><span data-stu-id="e67cd-120">Dangerous Permissions and Policy Administration</span></span>](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="e67cd-121">Discute algumas permissões do .NET Framework que podem potencialmente permitir que o sistema de segurança seja contornado.</span><span class="sxs-lookup"><span data-stu-id="e67cd-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="e67cd-122">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="e67cd-122">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="e67cd-123">Fornece links para tópicos que explicam as práticas recomendadas para escrever código com segurança no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e67cd-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="e67cd-124">[Solicitando permissões](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e67cd-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="e67cd-125">Discute o uso de atributos que permitem que o tempo de execução saiba quais permissões seu código precisa executar.</span><span class="sxs-lookup"><span data-stu-id="e67cd-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="e67cd-126">Principais conceitos de segurança</span><span class="sxs-lookup"><span data-stu-id="e67cd-126">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="e67cd-127">Links para tópicos que abrangem aspectos básicos de segurança de código.</span><span class="sxs-lookup"><span data-stu-id="e67cd-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="e67cd-128">Noções Básicas da Segurança de Acesso do Código</span><span class="sxs-lookup"><span data-stu-id="e67cd-128">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 <span data-ttu-id="e67cd-129">Discute as noções básicas de trabalhar com a política de segurança de tempo de execução do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e67cd-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="e67cd-130">[Determinando quando modificar a política de segurança](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e67cd-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="e67cd-131">Explica como determinar quando seus aplicativos precisam divergir da política de segurança padrão.</span><span class="sxs-lookup"><span data-stu-id="e67cd-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="e67cd-132">[Implantar política de segurança](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e67cd-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="e67cd-133">Discute a melhor maneira de implantar alterações de política de segurança.</span><span class="sxs-lookup"><span data-stu-id="e67cd-133">Discusses the best manner for deploying security policy changes.</span></span>
