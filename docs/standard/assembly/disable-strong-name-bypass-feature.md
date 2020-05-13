---
title: Como desabilitar o recurso de bypass de nome forte
description: O bypass de nome forte ignora a validação de assinatura em domínios totalmente confiáveis no .NET. Você pode substituir esse recurso para um único aplicativo ou todos os aplicativos.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: 1914997b322591d8deda13d00192bc5f60d81ca2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378488"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="d3b78-104">Como desabilitar o recurso de bypass de nome forte</span><span class="sxs-lookup"><span data-stu-id="d3b78-104">How to: Disable the strong-name bypass feature</span></span>
<span data-ttu-id="d3b78-105">Desde o .NET Framework versão 3.5 Service Pack 1 (SP1), as assinaturas de nome forte não são validadas quando um assembly é carregado em um objeto <xref:System.AppDomain> de confiança total, como o <xref:System.AppDomain> padrão para a zona `MyComputer`.</span><span class="sxs-lookup"><span data-stu-id="d3b78-105">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="d3b78-106">Isso é conhecido como o recurso de desvio de nome forte.</span><span class="sxs-lookup"><span data-stu-id="d3b78-106">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="d3b78-107">Em um ambiente de confiança total, as exigências de <xref:System.Security.Permissions.StrongNameIdentityPermission> sempre têm êxito para assemblies assinados de confiança total, independentemente de sua assinatura.</span><span class="sxs-lookup"><span data-stu-id="d3b78-107">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="d3b78-108">A única restrição é que o assembly deve ser totalmente confiável porque sua zona é totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="d3b78-108">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="d3b78-109">Como o nome forte não é um fator determinante sob essas condições, não há nenhum motivo para ser validado.</span><span class="sxs-lookup"><span data-stu-id="d3b78-109">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="d3b78-110">Ignorar a validação de assinaturas de nome forte fornece melhorias significativas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="d3b78-110">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="d3b78-111">O recurso de desvio se aplica a qualquer assembly de confiança total que não é assinado com atraso e que é carregado em qualquer <xref:System.AppDomain> de confiança total no diretório especificado por sua propriedade <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3b78-111">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="d3b78-112">Você pode substituir o recurso de desvio para todos os aplicativos em um computador definindo um valor de chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="d3b78-112">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="d3b78-113">Você pode substituir a configuração de um único aplicativo usando um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3b78-113">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="d3b78-114">Você não poderá restabelecer o recurso de desvio para um único aplicativo se ele tiver sido desabilitado pela chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="d3b78-114">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="d3b78-115">Quando você substitui o recurso de desvio, o nome forte é validado somente para correção, ele não é verificado para um <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="d3b78-115">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="d3b78-116">Se você quiser confirmar um nome forte específico, precisará executar essa verificação separadamente.</span><span class="sxs-lookup"><span data-stu-id="d3b78-116">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d3b78-117">A capacidade de forçar a validação de nome forte depende de uma chave do Registro, conforme descrito no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="d3b78-117">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="d3b78-118">Se um aplicativo estiver em execução em uma conta que não tem permissão da ACL (lista de controle de acesso) para acessar essa chave do Registro, a configuração é ineficaz.</span><span class="sxs-lookup"><span data-stu-id="d3b78-118">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="d3b78-119">Você deve garantir que os direitos da ACL estejam configurados para essa chave para que ela possa ser lida por todos os assemblies.</span><span class="sxs-lookup"><span data-stu-id="d3b78-119">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="d3b78-120">Desabilitar o recurso de bypass de nome forte para todos os aplicativos</span><span class="sxs-lookup"><span data-stu-id="d3b78-120">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="d3b78-121">Em computadores de 32 bits, no Registro do sistema, crie uma entrada DWORD com um valor de 0 chamada `AllowStrongNameBypass` sob a chave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework.</span><span class="sxs-lookup"><span data-stu-id="d3b78-121">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="d3b78-122">Em computadores de 64 bits, no Registro do sistema, crie uma entrada DWORD com um valor de 0 chamada `AllowStrongNameBypass` sob as chaves HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework e HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework.</span><span class="sxs-lookup"><span data-stu-id="d3b78-122">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="d3b78-123">Desabilitar o recurso de bypass de nome forte para um único aplicativo</span><span class="sxs-lookup"><span data-stu-id="d3b78-123">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="d3b78-124">Abra ou crie o arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3b78-124">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="d3b78-125">Para obter mais informações sobre esse arquivo, consulte a seção arquivos de configuração de aplicativo em [configurar aplicativos](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="d3b78-125">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="d3b78-126">Adicione a seguinte entrada:</span><span class="sxs-lookup"><span data-stu-id="d3b78-126">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="d3b78-127">Você pode restaurar o recurso de bypass para o aplicativo removendo a configuração do arquivo de configuração ou definindo o atributo como `true` .</span><span class="sxs-lookup"><span data-stu-id="d3b78-127">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3b78-128">Você poderá ligar e desligar a validação de nome forte para um aplicativo somente se o recurso de desvio estiver habilitado para o computador.</span><span class="sxs-lookup"><span data-stu-id="d3b78-128">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="d3b78-129">Se o recurso de desvio foi desativado para o computador, os nomes fortes são validados para todos os aplicativos e você não pode ignorar a validação para um único aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3b78-129">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b78-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="d3b78-130">See also</span></span>

- [<span data-ttu-id="d3b78-131">Sn. exe (ferramenta Strong Name)</span><span class="sxs-lookup"><span data-stu-id="d3b78-131">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="d3b78-132">\<elemento de> bypassTrustedAppStrongNames</span><span class="sxs-lookup"><span data-stu-id="d3b78-132">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="d3b78-133">Criar e usar assemblies com nome forte</span><span class="sxs-lookup"><span data-stu-id="d3b78-133">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
