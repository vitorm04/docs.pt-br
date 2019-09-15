---
title: 'Como: Desabilitar o recurso de bypass de nome forte'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8cdc700ecc8195da1b5e0975f00a4dc6785d330
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973288"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="68b8c-102">Como: Desabilitar o recurso de bypass de nome forte</span><span class="sxs-lookup"><span data-stu-id="68b8c-102">How to: Disable the strong-name bypass feature</span></span>
<span data-ttu-id="68b8c-103">Desde o .NET Framework versão 3.5 Service Pack 1 (SP1), as assinaturas de nome forte não são validadas quando um assembly é carregado em um objeto <xref:System.AppDomain> de confiança total, como o <xref:System.AppDomain> padrão para a zona `MyComputer`.</span><span class="sxs-lookup"><span data-stu-id="68b8c-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="68b8c-104">Isso é conhecido como o recurso de desvio de nome forte.</span><span class="sxs-lookup"><span data-stu-id="68b8c-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="68b8c-105">Em um ambiente de confiança total, as exigências de <xref:System.Security.Permissions.StrongNameIdentityPermission> sempre têm êxito para assemblies assinados de confiança total, independentemente de sua assinatura.</span><span class="sxs-lookup"><span data-stu-id="68b8c-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="68b8c-106">A única restrição é que o assembly deve ser totalmente confiável porque sua zona é totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="68b8c-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="68b8c-107">Como o nome forte não é um fator determinante sob essas condições, não há nenhum motivo para ser validado.</span><span class="sxs-lookup"><span data-stu-id="68b8c-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="68b8c-108">Ignorar a validação de assinaturas de nome forte fornece melhorias significativas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="68b8c-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="68b8c-109">O recurso de desvio se aplica a qualquer assembly de confiança total que não é assinado com atraso e que é carregado em qualquer <xref:System.AppDomain> de confiança total no diretório especificado por sua propriedade <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="68b8c-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="68b8c-110">Você pode substituir o recurso de desvio para todos os aplicativos em um computador definindo um valor de chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="68b8c-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="68b8c-111">Você pode substituir a configuração de um único aplicativo usando um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="68b8c-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="68b8c-112">Você não poderá restabelecer o recurso de desvio para um único aplicativo se ele tiver sido desabilitado pela chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="68b8c-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="68b8c-113">Quando você substitui o recurso de desvio, o nome forte é validado somente para correção, ele não é verificado para um <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="68b8c-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="68b8c-114">Se você quiser confirmar um nome forte específico, precisará executar essa verificação separadamente.</span><span class="sxs-lookup"><span data-stu-id="68b8c-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="68b8c-115">A capacidade de forçar a validação de nome forte depende de uma chave do Registro, conforme descrito no procedimento a seguir.</span><span class="sxs-lookup"><span data-stu-id="68b8c-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="68b8c-116">Se um aplicativo estiver em execução em uma conta que não tem permissão da ACL (lista de controle de acesso) para acessar essa chave do Registro, a configuração é ineficaz.</span><span class="sxs-lookup"><span data-stu-id="68b8c-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="68b8c-117">Você deve garantir que os direitos da ACL estejam configurados para essa chave para que ela possa ser lida por todos os assemblies.</span><span class="sxs-lookup"><span data-stu-id="68b8c-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="68b8c-118">Desabilitar o recurso de bypass de nome forte para todos os aplicativos</span><span class="sxs-lookup"><span data-stu-id="68b8c-118">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="68b8c-119">Em computadores de 32 bits, no Registro do sistema, crie uma entrada DWORD com um valor de 0 chamada `AllowStrongNameBypass` sob a chave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework.</span><span class="sxs-lookup"><span data-stu-id="68b8c-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="68b8c-120">Em computadores de 64 bits, no Registro do sistema, crie uma entrada DWORD com um valor de 0 chamada `AllowStrongNameBypass` sob as chaves HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework e HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework.</span><span class="sxs-lookup"><span data-stu-id="68b8c-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="68b8c-121">Desabilitar o recurso de bypass de nome forte para um único aplicativo</span><span class="sxs-lookup"><span data-stu-id="68b8c-121">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="68b8c-122">Abra ou crie o arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="68b8c-122">Open or create the application configuration file.</span></span>  
  
     <span data-ttu-id="68b8c-123">Para obter mais informações sobre esse arquivo, consulte a seção arquivos de configuração de aplicativo em [configurar aplicativos](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="68b8c-123">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="68b8c-124">Adicione a seguinte entrada:</span><span class="sxs-lookup"><span data-stu-id="68b8c-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="68b8c-125">Você pode restaurar o recurso de bypass para o aplicativo removendo a configuração do arquivo de configuração ou definindo o `true`atributo como.</span><span class="sxs-lookup"><span data-stu-id="68b8c-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68b8c-126">Você poderá ligar e desligar a validação de nome forte para um aplicativo somente se o recurso de desvio estiver habilitado para o computador.</span><span class="sxs-lookup"><span data-stu-id="68b8c-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="68b8c-127">Se o recurso de desvio foi desativado para o computador, os nomes fortes são validados para todos os aplicativos e você não pode ignorar a validação para um único aplicativo.</span><span class="sxs-lookup"><span data-stu-id="68b8c-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68b8c-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68b8c-128">See also</span></span>

- [<span data-ttu-id="68b8c-129">Sn.exe (Ferramenta Nome Forte)</span><span class="sxs-lookup"><span data-stu-id="68b8c-129">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="68b8c-130">\<elemento de > bypassTrustedAppStrongNames</span><span class="sxs-lookup"><span data-stu-id="68b8c-130">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="68b8c-131">Criar e usar assemblies de nome forte</span><span class="sxs-lookup"><span data-stu-id="68b8c-131">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
