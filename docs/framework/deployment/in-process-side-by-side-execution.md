---
title: Execução lado a lado em processo
description: Use a hospedagem no processo lado a lado para executar muitas versões do Common Language Runtime (CLR) em um único processo .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
ms.openlocfilehash: 078f2eaada8fac57138bef22d46218ef2ccda835
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622595"
---
# <a name="in-process-side-by-side-execution"></a><span data-ttu-id="8f95c-103">Execução lado a lado em processo</span><span class="sxs-lookup"><span data-stu-id="8f95c-103">In-Process Side-by-Side Execution</span></span>
<span data-ttu-id="8f95c-104">A partir do .NET Framework 4, você pode usar a hospedagem lado a lado em processo para executar várias versões do CLR (Common Language Runtime) em um único processo.</span><span class="sxs-lookup"><span data-stu-id="8f95c-104">Starting with the .NET Framework 4, you can use in-process side-by-side hosting to run multiple versions of the common language runtime (CLR) in a single process.</span></span> <span data-ttu-id="8f95c-105">Por padrão, os componentes COM gerenciados são executados com a versão do .NET Framework com a qual eles foram criados, independentemente da versão do .NET Framework carregada para o processo.</span><span class="sxs-lookup"><span data-stu-id="8f95c-105">By default, managed COM components run with the .NET Framework version they were built with, regardless of the .NET Framework version that is loaded for the process.</span></span>  
  
## <a name="background"></a><span data-ttu-id="8f95c-106">Segundo plano</span><span class="sxs-lookup"><span data-stu-id="8f95c-106">Background</span></span>  
 <span data-ttu-id="8f95c-107">O .NET Framework sempre forneceu a hospedagem lado a lado para aplicativos de código gerenciado, mas antes do .NET Framework 4, ele não fornecia essa funcionalidade para componentes COM gerenciados.</span><span class="sxs-lookup"><span data-stu-id="8f95c-107">The .NET Framework has always provided side-by-side hosting for managed code applications, but before the .NET Framework 4, it did not provide that functionality for managed COM components.</span></span> <span data-ttu-id="8f95c-108">No passado, os componentes COM gerenciados que eram carregados em um processo eram executados com a versão do runtime que já estava carregada ou com a versão mais recente instalada do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f95c-108">In the past, managed COM components that were loaded into a process ran either with the version of the runtime that was already loaded or with the latest installed version of the .NET Framework.</span></span> <span data-ttu-id="8f95c-109">Se essa versão não era compatível com o componente COM, ele falhava.</span><span class="sxs-lookup"><span data-stu-id="8f95c-109">If this version was not compatible with the COM component, the component would fail.</span></span>  
  
 <span data-ttu-id="8f95c-110">O .NET Framework 4 fornece uma nova abordagem para hospedagem lado a lado que garante o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8f95c-110">The .NET Framework 4 provides a new approach to side-by-side hosting that ensures the following:</span></span>  
  
- <span data-ttu-id="8f95c-111">Instalar uma nova versão do .NET Framework não tem nenhum efeito em aplicativos existentes.</span><span class="sxs-lookup"><span data-stu-id="8f95c-111">Installing a new version of the .NET Framework has no effect on existing applications.</span></span>  
  
- <span data-ttu-id="8f95c-112">Os aplicativos são executados na versão do .NET Framework com a qual foram criados.</span><span class="sxs-lookup"><span data-stu-id="8f95c-112">Applications run against the version of the .NET Framework that they were built with.</span></span> <span data-ttu-id="8f95c-113">Eles não usar a nova versão do .NET Framework, exceto quando expressamente determinado para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="8f95c-113">They do not use the new version of the .NET Framework unless expressly directed to do so.</span></span> <span data-ttu-id="8f95c-114">No entanto, é mais fácil para os aplicativos fazerem a transição para usar uma nova versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f95c-114">However, it is easier for applications to transition to using a new version of the .NET Framework.</span></span>  
  
## <a name="effects-on-users-and-developers"></a><span data-ttu-id="8f95c-115">Efeitos em usuários e desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="8f95c-115">Effects on Users and Developers</span></span>  
  
- <span data-ttu-id="8f95c-116">**Usuários finais e administradores de sistema**.</span><span class="sxs-lookup"><span data-stu-id="8f95c-116">**End users and system administrators**.</span></span> <span data-ttu-id="8f95c-117">Esses usuários agora podem ter uma confiança maior de que quando instalarem uma nova versão do runtime, independentemente ou com um aplicativo, ela não terá impacto em seus computadores.</span><span class="sxs-lookup"><span data-stu-id="8f95c-117">These users can now have greater confidence that when they install a new version of the runtime, either independently or with an application, it will have no impact on their computers.</span></span> <span data-ttu-id="8f95c-118">Os aplicativos existentes continuarão a ser executados como eram antes.</span><span class="sxs-lookup"><span data-stu-id="8f95c-118">Existing applications will continue to run as they did before.</span></span>  
  
- <span data-ttu-id="8f95c-119">**Desenvolvedores de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="8f95c-119">**Application developers**.</span></span> <span data-ttu-id="8f95c-120">A hospedagem lado a lado quase não tem efeito sobre os desenvolvedores de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8f95c-120">Side-by-side hosting has almost no effect on application developers.</span></span> <span data-ttu-id="8f95c-121">Por padrão, os aplicativos sempre são executados na versão do .NET Framework em que foram criados, isso não mudou.</span><span class="sxs-lookup"><span data-stu-id="8f95c-121">By default, applications always run against the version of the .NET Framework they were built on; this has not changed.</span></span> <span data-ttu-id="8f95c-122">No entanto, os desenvolvedores podem substituir esse comportamento e direcionar o aplicativo para ser executado em uma versão mais recente do .NET Framework (consulte o [cenário 2](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="8f95c-122">However, developers can override this behavior and direct the application to run under a newer version of the .NET Framework (see [scenario 2](#scenarios)).</span></span>  
  
- <span data-ttu-id="8f95c-123">**Desenvolvedores de bibliotecas e consumidores**.</span><span class="sxs-lookup"><span data-stu-id="8f95c-123">**Library developers and consumers**.</span></span> <span data-ttu-id="8f95c-124">A hospedagem lado a lado não resolve os problemas de compatibilidade que os desenvolvedores de bibliotecas enfrentam.</span><span class="sxs-lookup"><span data-stu-id="8f95c-124">Side-by-side hosting does not solve the compatibility problems that library developers face.</span></span> <span data-ttu-id="8f95c-125">Uma biblioteca que é carregada diretamente por um aplicativo, por meio de uma referência direta ou uma chamada <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, continua a usar o runtime do <xref:System.AppDomain> em que foi carregada.</span><span class="sxs-lookup"><span data-stu-id="8f95c-125">A library that is directly loaded by an application -- either through a direct reference or through an <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> call -- continues to use the runtime of the <xref:System.AppDomain> it is loaded into.</span></span> <span data-ttu-id="8f95c-126">Você deve testar suas bibliotecas em todas as versões do .NET Framework para as quais você deseja dar suporte.</span><span class="sxs-lookup"><span data-stu-id="8f95c-126">You should test your libraries against all versions of the .NET Framework that you want to support.</span></span> <span data-ttu-id="8f95c-127">Se um aplicativo for compilado usando o runtime do .NET Framework 4, mas incluir uma biblioteca que foi criada usando um runtime anterior, essa biblioteca também usará o runtime do .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8f95c-127">If an application is compiled using the .NET Framework 4 runtime but includes a library that was built using an earlier runtime, that library will use the .NET Framework 4 runtime as well.</span></span> <span data-ttu-id="8f95c-128">No entanto, se você tiver um aplicativo que foi criado usando um runtime mais recente e a biblioteca que foi criada usando o .NET Framework 4, será necessário forçar o aplicativo a também usar o .NET Framework 4 (consulte o [cenário 3](#scenarios)).</span><span class="sxs-lookup"><span data-stu-id="8f95c-128">However, if you have an application that was built using an earlier runtime and a library that was built using the .NET Framework 4, you must force your application to also use the .NET Framework 4 (see [scenario 3](#scenarios)).</span></span>  
  
- <span data-ttu-id="8f95c-129">**Desenvolvedores de componente COM gerenciado**.</span><span class="sxs-lookup"><span data-stu-id="8f95c-129">**Managed COM component developers**.</span></span> <span data-ttu-id="8f95c-130">No passado, componentes COM gerenciados eram executados automaticamente usando a versão mais recente do runtime instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="8f95c-130">In the past, managed COM components automatically ran using the latest version of the runtime installed on the computer.</span></span> <span data-ttu-id="8f95c-131">Agora você pode executar componentes COM na versão do runtime em que eles foram criados.</span><span class="sxs-lookup"><span data-stu-id="8f95c-131">You can now execute COM components against the version of the runtime they were built with.</span></span>  
  
     <span data-ttu-id="8f95c-132">Conforme mostrado pela tabela a seguir, os componentes que foram criados com o .NET Framework versão 1.1 podem ser executados lado a lado com os componentes da versão 4, mas não podem ser executados com componentes da versão 2.0, 3.0 ou 3.5, pois a hospedagem lado a lado não está disponível para essas versões.</span><span class="sxs-lookup"><span data-stu-id="8f95c-132">As shown by the following table, components that were built with the .NET Framework version 1.1 can run side by side with version 4 components, but they cannot run with version 2.0, 3.0, or 3.5 components, because side-by-side hosting is not available for those versions.</span></span>  
  
    |<span data-ttu-id="8f95c-133">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8f95c-133">.NET Framework version</span></span>|<span data-ttu-id="8f95c-134">1,1</span><span class="sxs-lookup"><span data-stu-id="8f95c-134">1.1</span></span>|<span data-ttu-id="8f95c-135">2.0 – 3.5</span><span class="sxs-lookup"><span data-stu-id="8f95c-135">2.0 - 3.5</span></span>|<span data-ttu-id="8f95c-136">4</span><span class="sxs-lookup"><span data-stu-id="8f95c-136">4</span></span>|  
    |----------------------------|---------|----------------|-------|  
    |<span data-ttu-id="8f95c-137">1,1</span><span class="sxs-lookup"><span data-stu-id="8f95c-137">1.1</span></span>|<span data-ttu-id="8f95c-138">Não Aplicável</span><span class="sxs-lookup"><span data-stu-id="8f95c-138">Not applicable</span></span>|<span data-ttu-id="8f95c-139">Não</span><span class="sxs-lookup"><span data-stu-id="8f95c-139">No</span></span>|<span data-ttu-id="8f95c-140">Sim</span><span class="sxs-lookup"><span data-stu-id="8f95c-140">Yes</span></span>|  
    |<span data-ttu-id="8f95c-141">2.0 – 3.5</span><span class="sxs-lookup"><span data-stu-id="8f95c-141">2.0 - 3.5</span></span>|<span data-ttu-id="8f95c-142">Não</span><span class="sxs-lookup"><span data-stu-id="8f95c-142">No</span></span>|<span data-ttu-id="8f95c-143">Não aplicável</span><span class="sxs-lookup"><span data-stu-id="8f95c-143">Not applicable</span></span>|<span data-ttu-id="8f95c-144">Sim</span><span class="sxs-lookup"><span data-stu-id="8f95c-144">Yes</span></span>|  
    |<span data-ttu-id="8f95c-145">4</span><span class="sxs-lookup"><span data-stu-id="8f95c-145">4</span></span>|<span data-ttu-id="8f95c-146">Sim</span><span class="sxs-lookup"><span data-stu-id="8f95c-146">Yes</span></span>|<span data-ttu-id="8f95c-147">Sim</span><span class="sxs-lookup"><span data-stu-id="8f95c-147">Yes</span></span>|<span data-ttu-id="8f95c-148">Não Aplicável</span><span class="sxs-lookup"><span data-stu-id="8f95c-148">Not applicable</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="8f95c-149">As versões 3.0 e 3.5 do .NET Framework são criadas de forma incremental na versão 2.0 e não precisam ser executadas lado a lado.</span><span class="sxs-lookup"><span data-stu-id="8f95c-149">.NET Framework versions 3.0 and 3.5 are built incrementally on version 2.0, and do not need to run side by side.</span></span> <span data-ttu-id="8f95c-150">Elas são inerentemente a mesma versão.</span><span class="sxs-lookup"><span data-stu-id="8f95c-150">These are inherently the same version.</span></span>  
  
<a name="scenarios"></a>
## <a name="common-side-by-side-hosting-scenarios"></a><span data-ttu-id="8f95c-151">Cenários comuns de hospedagem lado a lado</span><span class="sxs-lookup"><span data-stu-id="8f95c-151">Common Side-by-Side Hosting Scenarios</span></span>  
  
- <span data-ttu-id="8f95c-152">**Cenário 1:** aplicativo nativo que usa componentes COM criados com versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f95c-152">**Scenario 1:** Native application that uses COM components built with earlier versions of the .NET Framework.</span></span>  
  
     <span data-ttu-id="8f95c-153">.NET Framework versões instaladas: a .NET Framework 4 e todas as outras versões do .NET Framework usadas pelos componentes COM.</span><span class="sxs-lookup"><span data-stu-id="8f95c-153">.NET Framework versions installed: The .NET Framework 4 and all other versions of the .NET Framework used by the COM components.</span></span>  
  
     <span data-ttu-id="8f95c-154">O que fazer: nesse cenário, não faça nada.</span><span class="sxs-lookup"><span data-stu-id="8f95c-154">What to do: In this scenario, do nothing.</span></span> <span data-ttu-id="8f95c-155">Os componentes COM serão executados com a versão do .NET Framework com a qual foram registrados.</span><span class="sxs-lookup"><span data-stu-id="8f95c-155">The COM components will run with the version of the .NET Framework they were registered with.</span></span>  
  
- <span data-ttu-id="8f95c-156">**Cenário 2**: aplicativo gerenciado criado com o .NET Framework 2,0 SP1 que você prefere executar com o .NET Framework 2,0, mas que está disposto a ser executado no .NET Framework 4 se a versão 2,0 não estiver presente.</span><span class="sxs-lookup"><span data-stu-id="8f95c-156">**Scenario 2**: Managed application built with the .NET Framework 2.0 SP1 that you would prefer to run with the .NET Framework 2.0, but are willing to run on the .NET Framework 4 if version 2.0 is not present.</span></span>  
  
     <span data-ttu-id="8f95c-157">.NET Framework versões instaladas: uma versão anterior do .NET Framework e o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8f95c-157">.NET Framework versions installed: An earlier version of the .NET Framework and the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="8f95c-158">O que fazer: no [arquivo de configuração do aplicativo](../configure-apps/index.md) no diretório do aplicativo, use o [ \<startup> elemento](../configure-apps/file-schema/startup/startup-element.md) e o [ \<supportedRuntime> elemento](../configure-apps/file-schema/startup/supportedruntime-element.md) definido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8f95c-158">What to do: In the [application configuration file](../configure-apps/index.md) in the application directory, use the [\<startup> element](../configure-apps/file-schema/startup/startup-element.md) and the [\<supportedRuntime> element](../configure-apps/file-schema/startup/supportedruntime-element.md) set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- <span data-ttu-id="8f95c-159">**Cenário 3:** Aplicativo nativo que usa componentes COM criados com versões anteriores do .NET Framework que você deseja executar com o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8f95c-159">**Scenario 3:** Native application that uses COM components built with earlier versions of the .NET Framework that you want to run with the .NET Framework 4.</span></span>  
  
     <span data-ttu-id="8f95c-160">.NET Framework versões instaladas: o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8f95c-160">.NET Framework versions installed: The .NET Framework 4.</span></span>  
  
     <span data-ttu-id="8f95c-161">O que fazer: no arquivo de configuração de aplicativo no diretório do aplicativo, use o elemento `<startup>` com o atributo `useLegacyV2RuntimeActivationPolicy` definido como `true` e o elemento `<supportedRuntime>` definido da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8f95c-161">What to do: In the application configuration file in the application directory, use the `<startup>` element with the `useLegacyV2RuntimeActivationPolicy` attribute set to `true` and the `<supportedRuntime>` element set as follows:</span></span>  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="8f95c-162">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f95c-162">Example</span></span>  
 <span data-ttu-id="8f95c-163">O exemplo a seguir demonstra um host COM não gerenciado que está executando um componente COM gerenciado usando a versão do .NET Framework que o componente foi compilado para usar.</span><span class="sxs-lookup"><span data-stu-id="8f95c-163">The following example demonstrates an unmanaged COM host that is running a managed COM component by using the version of the .NET Framework that the component was compiled to use.</span></span>  
  
 <span data-ttu-id="8f95c-164">Para executar o exemplo a seguir, compile e registre o seguinte componente COM gerenciado usando o .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="8f95c-164">To run the following example, compile and register the following managed COM component using the .NET Framework 3.5.</span></span> <span data-ttu-id="8f95c-165">Para registrar o componente, no menu **Projeto**, clique em **Propriedades**, clique na guia **Compilar** e marque a caixa de seleção **Registrar para interoperabilidade COM**.</span><span class="sxs-lookup"><span data-stu-id="8f95c-165">To register the component, on the **Project** menu, click **Properties**, click the **Build** tab, and then select the **Register for COM interop** check box.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="8f95c-166">Compile o seguinte aplicativo C++ não gerenciado, que ativa o objeto COM criado pelo exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="8f95c-166">Compile the following unmanaged C++ application, which activates the COM object that is created by the previous example.</span></span>  
  
```cpp
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f95c-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f95c-167">See also</span></span>

- [<span data-ttu-id="8f95c-168">\<startup>Elementos</span><span class="sxs-lookup"><span data-stu-id="8f95c-168">\<startup> Element</span></span>](../configure-apps/file-schema/startup/startup-element.md)
- [<span data-ttu-id="8f95c-169">\<supportedRuntime>Elementos</span><span class="sxs-lookup"><span data-stu-id="8f95c-169">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
