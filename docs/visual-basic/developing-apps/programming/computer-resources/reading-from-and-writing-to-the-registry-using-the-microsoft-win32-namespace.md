---
title: Lendo e gravando no Registro usando o namespace Microsoft.Win32 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 6309f312ed05f48e65b19d8827322071cad1f6de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588863"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="56d56-102">Lendo e gravando no Registro usando o namespace Microsoft.Win32 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56d56-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>
<span data-ttu-id="56d56-103">`My.Computer.Registry` deve suprir suas necessidades básicas ao programar no registro, mas você também pode usar as classes <xref:Microsoft.Win32.Registry> e <xref:Microsoft.Win32.RegistryKey> do namespace <xref:Microsoft.Win32> do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56d56-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="56d56-104">Chaves na classe de Registro</span><span class="sxs-lookup"><span data-stu-id="56d56-104">Keys in the Registry Class</span></span>  
 <span data-ttu-id="56d56-105">A classe <xref:Microsoft.Win32.Registry> fornece as chaves base do Registro que podem ser usadas para acessar subchaves e seus valores.</span><span class="sxs-lookup"><span data-stu-id="56d56-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="56d56-106">As chaves base em si são somente leitura.</span><span class="sxs-lookup"><span data-stu-id="56d56-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="56d56-107">A tabela a seguir lista e descreve as sete chaves expostas pela classe <xref:Microsoft.Win32.Registry>.</span><span class="sxs-lookup"><span data-stu-id="56d56-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="56d56-108">**Chave**</span><span class="sxs-lookup"><span data-stu-id="56d56-108">**Key**</span></span>|<span data-ttu-id="56d56-109">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="56d56-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="56d56-110">Define os tipos de documentos e as propriedades associadas a esses tipos.</span><span class="sxs-lookup"><span data-stu-id="56d56-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="56d56-111">Contém informações de configuração de hardware que não são específicas do usuário.</span><span class="sxs-lookup"><span data-stu-id="56d56-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="56d56-112">Contém informações sobre as preferências do usuário atual, como variáveis ambientais.</span><span class="sxs-lookup"><span data-stu-id="56d56-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="56d56-113">Contém dados do registro dinâmico, como aqueles usados por Drivers de dispositivo virtual.</span><span class="sxs-lookup"><span data-stu-id="56d56-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="56d56-114">Contém cinco subchaves (Hardware, SAM, Segurança, Software e Sistema) que armazenam os dados de configuração do computador local.</span><span class="sxs-lookup"><span data-stu-id="56d56-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="56d56-115">Contém informações de desempenho de componentes de software.</span><span class="sxs-lookup"><span data-stu-id="56d56-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="56d56-116">Contém informações sobre as preferências do usuário padrão.</span><span class="sxs-lookup"><span data-stu-id="56d56-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="56d56-117">É mais seguro gravar dados na pasta do usuário atual (<xref:Microsoft.Win32.Registry.CurrentUser>) do que no computador local (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="56d56-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="56d56-118">Uma condição que costuma ser chamada de "squatting" ocorre quando a chave que você está criando foi criada anteriormente por outro processo, possivelmente mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="56d56-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="56d56-119">Para evitar que isso ocorra, use um método, como <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, que retornará `Nothing` se a chave ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="56d56-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="56d56-120">Lendo um valor do Registro</span><span class="sxs-lookup"><span data-stu-id="56d56-120">Reading a Value from the Registry</span></span>  
 <span data-ttu-id="56d56-121">O código a seguir mostra como ler uma cadeia de caracteres de HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="56d56-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_1.vb)]  
  
 <span data-ttu-id="56d56-122">O código a seguir lê, incrementa e grava uma cadeia de caracteres em HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="56d56-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="56d56-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56d56-123">See Also</span></span>  
 <xref:System.SystemException>  
 <xref:System.ApplicationException>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [<span data-ttu-id="56d56-124">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="56d56-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="56d56-125">Lendo e Gravando do Registro</span><span class="sxs-lookup"><span data-stu-id="56d56-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [<span data-ttu-id="56d56-126">Segurança e Registro</span><span class="sxs-lookup"><span data-stu-id="56d56-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
