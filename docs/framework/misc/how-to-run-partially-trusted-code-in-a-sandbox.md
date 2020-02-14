---
title: Como executar código parcialmente confiável em uma área restrita
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: 0191846f5589b0162ba342161fb5919ff20099d4
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215856"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="11482-102">Como executar código parcialmente confiável em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="11482-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="11482-103">A área restrita é a prática de executar código em um ambiente de segurança restrito, que limita as permissões de acesso concedidas ao código.</span><span class="sxs-lookup"><span data-stu-id="11482-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="11482-104">Por exemplo, se você tiver uma biblioteca gerenciada de uma fonte que não confia completamente, não deverá executá-la como totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="11482-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="11482-105">Em vez disso, você deve colocar o código em uma área restrita que limita suas permissões para aqueles que você espera que sejam necessários (por exemplo, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão).</span><span class="sxs-lookup"><span data-stu-id="11482-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="11482-106">Você também pode usar a área restrita para testar o código que será distribuído e que será executado em ambientes parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="11482-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="11482-107">Uma <xref:System.AppDomain> é uma maneira eficaz de fornecer uma área restrita para aplicativos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="11482-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="11482-108">Os domínios de aplicativo usados para executar código parcialmente confiável têm permissões que definem os recursos protegidos que estão disponíveis durante a execução dentro desse <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="11482-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="11482-109">O código que é executado dentro do <xref:System.AppDomain> é associado pelas permissões associadas ao <xref:System.AppDomain> e tem permissão para acessar apenas os recursos especificados.</span><span class="sxs-lookup"><span data-stu-id="11482-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="11482-110">O <xref:System.AppDomain> também inclui uma matriz de <xref:System.Security.Policy.StrongName> que é usada para identificar assemblies que devem ser carregados como totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="11482-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="11482-111">Isso permite que o criador de um <xref:System.AppDomain> inicie um novo domínio em área restrita que permite que assemblies auxiliares específicos sejam totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="11482-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="11482-112">Outra opção para carregar assemblies como totalmente confiável é colocá-los no cache de assembly global; no entanto, isso carregará os assemblies como totalmente confiáveis em todos os domínios de aplicativo criados nesse computador.</span><span class="sxs-lookup"><span data-stu-id="11482-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="11482-113">A lista de nomes fortes dá suporte a uma decisão por<xref:System.AppDomain> que fornece uma determinação mais restritiva.</span><span class="sxs-lookup"><span data-stu-id="11482-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="11482-114">Você pode usar a sobrecarga do método de <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> para especificar o conjunto de permissões para aplicativos que são executados em uma área restrita.</span><span class="sxs-lookup"><span data-stu-id="11482-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="11482-115">Essa sobrecarga permite que você especifique o nível exato de segurança de acesso do código desejado.</span><span class="sxs-lookup"><span data-stu-id="11482-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="11482-116">Os assemblies que são carregados em um <xref:System.AppDomain> usando essa sobrecarga podem ter apenas o Grant Set especificado ou podem ser totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="11482-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="11482-117">O assembly terá confiança total se estiver no cache de assembly global ou listado no parâmetro de matriz `fullTrustAssemblies` (<xref:System.Security.Policy.StrongName>).</span><span class="sxs-lookup"><span data-stu-id="11482-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="11482-118">Somente os assemblies conhecidos como totalmente confiáveis devem ser adicionados à lista de `fullTrustAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="11482-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="11482-119">A sobrecarga tem a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="11482-119">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="11482-120">Os parâmetros para a sobrecarga do método de <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> especificam o nome do <xref:System.AppDomain>, a evidência para o <xref:System.AppDomain>, o objeto <xref:System.AppDomainSetup> que identifica a base do aplicativo para a área restrita, o conjunto de permissões a ser usado e os nomes fortes para assemblies totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="11482-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="11482-121">Por motivos de segurança, a base do aplicativo especificada no parâmetro `info` não deve ser a base do aplicativo para o aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="11482-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="11482-122">Para o parâmetro `grantSet`, você pode especificar um conjunto de permissões que você criou explicitamente ou um conjunto de permissões padrão criado pelo método <xref:System.Security.SecurityManager.GetStandardSandbox%2A>.</span><span class="sxs-lookup"><span data-stu-id="11482-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="11482-123">Ao contrário da maioria das cargas de <xref:System.AppDomain>, a evidência da <xref:System.AppDomain> (que é fornecida pelo parâmetro `securityInfo`) não é usada para determinar o conjunto de concessão para os assemblies parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="11482-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="11482-124">Em vez disso, ele é especificado de forma independente pelo parâmetro `grantSet`.</span><span class="sxs-lookup"><span data-stu-id="11482-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="11482-125">No entanto, a evidência pode ser usada para outras finalidades, como determinar o escopo de armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="11482-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="11482-126">Para executar um aplicativo em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="11482-126">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="11482-127">Crie o conjunto de permissões a ser concedido ao aplicativo não confiável.</span><span class="sxs-lookup"><span data-stu-id="11482-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="11482-128">A permissão mínima que você pode conceder é <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão.</span><span class="sxs-lookup"><span data-stu-id="11482-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="11482-129">Você também pode conceder permissões adicionais que você ache que podem ser seguras para código não confiável; por exemplo, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="11482-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="11482-130">O código a seguir cria um novo conjunto de permissões com apenas <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão.</span><span class="sxs-lookup"><span data-stu-id="11482-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="11482-131">Como alternativa, você pode usar um conjunto de permissões nomeadas existente, como a Internet.</span><span class="sxs-lookup"><span data-stu-id="11482-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="11482-132">O método <xref:System.Security.SecurityManager.GetStandardSandbox%2A> retorna um conjunto de permissões `Internet` ou um conjunto de permissões `LocalIntranet` dependendo da zona na evidência.</span><span class="sxs-lookup"><span data-stu-id="11482-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="11482-133">o <xref:System.Security.SecurityManager.GetStandardSandbox%2A> também constrói permissões de identidade para alguns dos objetos de evidência passados como referências.</span><span class="sxs-lookup"><span data-stu-id="11482-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="11482-134">Assine o assembly que contém a classe de hospedagem (chamada `Sandboxer` neste exemplo) que chama o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="11482-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="11482-135">Adicione o <xref:System.Security.Policy.StrongName> usado para assinar o assembly para a matriz de <xref:System.Security.Policy.StrongName> do parâmetro `fullTrustAssemblies` da chamada <xref:System.AppDomain.CreateDomain%2A>.</span><span class="sxs-lookup"><span data-stu-id="11482-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="11482-136">A classe de hospedagem deve ser executada como totalmente confiável para habilitar a execução do código de confiança parcial ou para oferecer serviços ao aplicativo de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="11482-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="11482-137">É assim que você lê o <xref:System.Security.Policy.StrongName> de um assembly:</span><span class="sxs-lookup"><span data-stu-id="11482-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="11482-138">.NET Framework assemblies como mscorlib e System. dll não precisam ser adicionados à lista de confiança total porque eles são carregados como totalmente confiáveis do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="11482-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="11482-139">Inicialize o parâmetro <xref:System.AppDomainSetup> do método <xref:System.AppDomain.CreateDomain%2A>.</span><span class="sxs-lookup"><span data-stu-id="11482-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="11482-140">Com esse parâmetro, você pode controlar muitas das configurações do novo <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="11482-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="11482-141">A propriedade <xref:System.AppDomainSetup.ApplicationBase%2A> é uma configuração importante e deve ser diferente da propriedade <xref:System.AppDomainSetup.ApplicationBase%2A> para o <xref:System.AppDomain> do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="11482-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="11482-142">Se as configurações de <xref:System.AppDomainSetup.ApplicationBase%2A> forem as mesmas, o aplicativo de confiança parcial poderá fazer com que o aplicativo de hospedagem seja carregado (como totalmente confiável) uma exceção que ele define, explorando-o.</span><span class="sxs-lookup"><span data-stu-id="11482-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="11482-143">Essa é outra razão pela qual uma captura (exceção) não é recomendada.</span><span class="sxs-lookup"><span data-stu-id="11482-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="11482-144">Definir a base de aplicativos do host de forma diferente da base de aplicativos do aplicativo de área restrita reduz o risco de explorações.</span><span class="sxs-lookup"><span data-stu-id="11482-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="11482-145">Chame a sobrecarga do método de <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> para criar o domínio do aplicativo usando os parâmetros que especificamos.</span><span class="sxs-lookup"><span data-stu-id="11482-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="11482-146">A assinatura para esse método é:</span><span class="sxs-lookup"><span data-stu-id="11482-146">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="11482-147">Informações adicionais:</span><span class="sxs-lookup"><span data-stu-id="11482-147">Additional information:</span></span>  
  
    - <span data-ttu-id="11482-148">Essa é a única sobrecarga do método <xref:System.AppDomain.CreateDomain%2A> que usa um <xref:System.Security.PermissionSet> como um parâmetro e, portanto, a única sobrecarga que permite carregar um aplicativo em uma configuração de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="11482-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="11482-149">O parâmetro `evidence` não é usado para calcular um conjunto de permissões; Ele é usado para identificação por outros recursos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11482-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="11482-150">Definir a propriedade <xref:System.AppDomainSetup.ApplicationBase%2A> do parâmetro `info` é obrigatório para essa sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="11482-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="11482-151">O parâmetro `fullTrustAssemblies` tem a palavra-chave `params`, o que significa que não é necessário criar uma matriz <xref:System.Security.Policy.StrongName>.</span><span class="sxs-lookup"><span data-stu-id="11482-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="11482-152">Passar 0, 1 ou nomes mais fortes como parâmetros é permitido.</span><span class="sxs-lookup"><span data-stu-id="11482-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="11482-153">O código para criar o domínio do aplicativo é:</span><span class="sxs-lookup"><span data-stu-id="11482-153">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="11482-154">Carregue o código no <xref:System.AppDomain> de área restrita que você criou.</span><span class="sxs-lookup"><span data-stu-id="11482-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="11482-155">Isso pode ser feito de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="11482-155">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="11482-156">Chame o método <xref:System.AppDomain.ExecuteAssembly%2A> para o assembly.</span><span class="sxs-lookup"><span data-stu-id="11482-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="11482-157">Use o método <xref:System.Activator.CreateInstanceFrom%2A> para criar uma instância de uma classe derivada de <xref:System.MarshalByRefObject> no novo <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="11482-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="11482-158">O segundo método é preferível, pois torna mais fácil passar parâmetros para a nova instância de <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="11482-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="11482-159">O método <xref:System.Activator.CreateInstanceFrom%2A> fornece dois recursos importantes:</span><span class="sxs-lookup"><span data-stu-id="11482-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="11482-160">Você pode usar uma base de código que aponta para um local que não contém seu assembly.</span><span class="sxs-lookup"><span data-stu-id="11482-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="11482-161">Você pode fazer a criação em um <xref:System.Security.CodeAccessPermission.Assert%2A> para confiança total (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), que permite criar uma instância de uma classe crítica.</span><span class="sxs-lookup"><span data-stu-id="11482-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="11482-162">(Isso ocorre sempre que seu assembly não tem marcações de transparência e é carregado como totalmente confiável.) Portanto, você precisa ter cuidado para criar apenas o código em que confia com essa função e é recomendável criar apenas instâncias de classes totalmente confiáveis no novo domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11482-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="11482-163">Observe que para criar uma instância de uma classe em um novo domínio, a classe deve estender a classe de <xref:System.MarshalByRefObject></span><span class="sxs-lookup"><span data-stu-id="11482-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="11482-164">Desenvolva a nova instância de domínio em uma referência neste domínio.</span><span class="sxs-lookup"><span data-stu-id="11482-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="11482-165">Essa referência é usada para executar o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="11482-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="11482-166">Chame o método `ExecuteUntrustedCode` na instância da classe `Sandboxer` que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="11482-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="11482-167">Essa chamada é executada no domínio de aplicativo em área restrita, que tem permissões restritas.</span><span class="sxs-lookup"><span data-stu-id="11482-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is   
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <span data-ttu-id="11482-168"><xref:System.Reflection> é usado para obter um identificador de um método no assembly parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="11482-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="11482-169">O identificador pode ser usado para executar código de forma segura com permissões mínimas.</span><span class="sxs-lookup"><span data-stu-id="11482-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="11482-170">No código anterior, observe o <xref:System.Security.PermissionSet.Assert%2A> para a permissão de confiança total antes de imprimir o <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="11482-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="11482-171">A declaração de confiança total é usada para obter informações estendidas do <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="11482-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="11482-172">Sem o <xref:System.Security.PermissionSet.Assert%2A>, o método <xref:System.Security.SecurityException.ToString%2A> de <xref:System.Security.SecurityException> descobrirá que há código parcialmente confiável na pilha e restringirá as informações retornadas.</span><span class="sxs-lookup"><span data-stu-id="11482-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="11482-173">Isso poderá causar problemas de segurança se o código de confiança parcial pudesse ler essas informações, mas o risco for mitigado não concedendo <xref:System.Security.Permissions.UIPermission>.</span><span class="sxs-lookup"><span data-stu-id="11482-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="11482-174">A declaração de confiança total deve ser usada com moderação e somente quando você tiver certeza de que não está permitindo que o código de confiança parcial eleve a confiança total.</span><span class="sxs-lookup"><span data-stu-id="11482-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="11482-175">Como regra, não chame o código que você não confia na mesma função e depois de chamar uma declaração para confiança total.</span><span class="sxs-lookup"><span data-stu-id="11482-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="11482-176">É recomendável sempre reverter a declaração quando terminar de usá-la.</span><span class="sxs-lookup"><span data-stu-id="11482-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11482-177">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11482-177">Example</span></span>  
 <span data-ttu-id="11482-178">O exemplo a seguir implementa o procedimento na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="11482-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="11482-179">No exemplo, um projeto chamado `Sandboxer` em uma solução do Visual Studio também contém um projeto chamado `UntrustedCode`, que implementa a classe `UntrustedClass`.</span><span class="sxs-lookup"><span data-stu-id="11482-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="11482-180">Esse cenário pressupõe que você tenha baixado um assembly de biblioteca que contém um método que deve retornar `true` ou `false` para indicar se o número fornecido é um número Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="11482-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="11482-181">Em vez disso, o método tenta ler um arquivo do seu computador.</span><span class="sxs-lookup"><span data-stu-id="11482-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="11482-182">O exemplo a seguir mostra o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="11482-182">The following example shows the untrusted code.</span></span>  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="11482-183">O exemplo a seguir mostra o código do aplicativo `Sandboxer` que executa o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="11482-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another   
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder   
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to   
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.   
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the   
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are   
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="11482-184">Confira também</span><span class="sxs-lookup"><span data-stu-id="11482-184">See also</span></span>

- [<span data-ttu-id="11482-185">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="11482-185">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
