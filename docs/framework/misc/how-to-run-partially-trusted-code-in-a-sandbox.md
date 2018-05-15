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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05ab0874c980d9e6138ae2bfd720c6d89628613c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="d99fc-102">Como executar código parcialmente confiável em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="d99fc-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="d99fc-103">Modo seguro é a prática de execução de código em um ambiente de segurança restrito, o que limita as permissões de acesso concedidas ao código.</span><span class="sxs-lookup"><span data-stu-id="d99fc-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="d99fc-104">Por exemplo, se você tiver uma biblioteca gerenciada de uma fonte que não confiável completamente, você não deve executá-lo como totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="d99fc-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="d99fc-105">Em vez disso, você deve colocar o código em uma área restrita que limita suas permissões para aqueles que você espera que ele precisa (por exemplo, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão).</span><span class="sxs-lookup"><span data-stu-id="d99fc-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="d99fc-106">Você também pode usar o modo seguro para testar código você distribuirá que será executado nos ambientes parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="d99fc-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="d99fc-107">Um <xref:System.AppDomain> é uma maneira eficiente de fornecer uma área restrita para aplicativos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="d99fc-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="d99fc-108">Domínios de aplicativos que são usados para executar código parcialmente confiável têm permissões que definem os recursos protegidos que estão disponíveis durante a execução dentro desse <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="d99fc-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="d99fc-109">Código que é executado dentro do <xref:System.AppDomain> vinculado, as permissões associadas a <xref:System.AppDomain> e tem permissão para acessar somente os recursos especificados.</span><span class="sxs-lookup"><span data-stu-id="d99fc-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="d99fc-110">O <xref:System.AppDomain> também inclui um <xref:System.Security.Policy.StrongName> matriz que é usado para identificar os assemblies a ser carregado como totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="d99fc-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="d99fc-111">Isso permite que o criador de uma <xref:System.AppDomain> para iniciar um novo domínio em modo seguro que permite que os assemblies de auxiliar específico seja totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="d99fc-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="d99fc-112">Outra opção para carregar assemblies totalmente confiáveis é colocá-los no cache de assembly global; No entanto, que irá carregar assemblies como totalmente confiável em todos os domínios de aplicativo criados no computador.</span><span class="sxs-lookup"><span data-stu-id="d99fc-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="d99fc-113">A lista de alta segurança nomes dá suporte a um por-<xref:System.AppDomain> decisão que fornece determinação mais restritiva.</span><span class="sxs-lookup"><span data-stu-id="d99fc-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="d99fc-114">Você pode usar o <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> sobrecarga do método para especificar a permissão definida para aplicativos que são executados em uma área restrita.</span><span class="sxs-lookup"><span data-stu-id="d99fc-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="d99fc-115">Essa sobrecarga permite que você especifique o nível exato de segurança de acesso do código desejado.</span><span class="sxs-lookup"><span data-stu-id="d99fc-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="d99fc-116">Assemblies são carregados em um <xref:System.AppDomain> usando essa sobrecarga pode ter especificado conceder apenas conjunto, ou pode ser totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="d99fc-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="d99fc-117">O assembly é concedido confiança total, se ele estiver no cache de assembly global ou listados no `fullTrustAssemblies` (o <xref:System.Security.Policy.StrongName>) o parâmetro de matriz.</span><span class="sxs-lookup"><span data-stu-id="d99fc-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="d99fc-118">Apenas os assemblies conhecidos para ser totalmente confiáveis devem ser adicionados para o `fullTrustAssemblies` lista.</span><span class="sxs-lookup"><span data-stu-id="d99fc-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="d99fc-119">A sobrecarga tem a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="d99fc-119">The overload has the following signature:</span></span>  
  
```  
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="d99fc-120">Os parâmetros para o <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> sobrecarga do método de especificar o nome do <xref:System.AppDomain>, a evidência para o <xref:System.AppDomain>, o <xref:System.AppDomainSetup> objeto que identifica a base de dados de aplicativo para a área restrita, o conjunto de permissões para usar e os nomes de alta seguras para assemblies totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="d99fc-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="d99fc-121">Por motivos de segurança, a base de dados de aplicativo especificado no `info` parâmetro não deve ser a base para o aplicativo host do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d99fc-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="d99fc-122">Para o `grantSet` parâmetro, você pode especificar um conjunto de permissões que você criou explicitamente ou uma permissão padrão conjunto criado pelo <xref:System.Security.SecurityManager.GetStandardSandbox%2A> método.</span><span class="sxs-lookup"><span data-stu-id="d99fc-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="d99fc-123">Ao contrário da maioria <xref:System.AppDomain> carrega a evidência para o <xref:System.AppDomain> (que é fornecido pelo `securityInfo` parâmetro) não é usado para determinar a concessão definido para os assemblies parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="d99fc-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="d99fc-124">Em vez disso, ele é especificado pelo independentemente a `grantSet` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d99fc-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="d99fc-125">No entanto, a evidência pode ser usada para outras finalidades, como determinar o escopo do armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="d99fc-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="d99fc-126">Para executar um aplicativo em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="d99fc-126">To run an application in a sandbox</span></span>  
  
1.  <span data-ttu-id="d99fc-127">Crie conjunto de permissões para ser concedida ao aplicativo não confiável.</span><span class="sxs-lookup"><span data-stu-id="d99fc-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="d99fc-128">A permissão mínima, você pode conceder é <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão.</span><span class="sxs-lookup"><span data-stu-id="d99fc-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="d99fc-129">Você também pode conceder permissões adicionais que você acha que podem ser seguras para código não confiável. Por exemplo, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="d99fc-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="d99fc-130">O código a seguir cria um novo conjunto de permissões com apenas <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permissão.</span><span class="sxs-lookup"><span data-stu-id="d99fc-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```  
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="d99fc-131">Como alternativa, você pode usar um conjunto de permissões nomeadas existente, como a Internet.</span><span class="sxs-lookup"><span data-stu-id="d99fc-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="d99fc-132">O <xref:System.Security.SecurityManager.GetStandardSandbox%2A> método retorna um uma `Internet` conjunto de permissões ou uma `LocalIntranet` conjunto de permissões dependendo da zona na evidência.</span><span class="sxs-lookup"><span data-stu-id="d99fc-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="d99fc-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> constrói as permissões de identidade para alguns dos objetos de evidência passados como referências.</span><span class="sxs-lookup"><span data-stu-id="d99fc-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2.  <span data-ttu-id="d99fc-134">Assinar o assembly que contém a classe de hospedagem (chamada `Sandboxer` neste exemplo) que chama o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="d99fc-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="d99fc-135">Adicionar o <xref:System.Security.Policy.StrongName> usado para assinar o assembly para o <xref:System.Security.Policy.StrongName> matriz do `fullTrustAssemblies` parâmetro do <xref:System.AppDomain.CreateDomain%2A> chamar.</span><span class="sxs-lookup"><span data-stu-id="d99fc-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="d99fc-136">A classe de hospedagem deve ser executado como totalmente confiável para habilitar a execução do código parcialmente confiável ou para oferecer serviços para o aplicativo de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="d99fc-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="d99fc-137">Isso é como você ler o <xref:System.Security.Policy.StrongName> de um assembly:</span><span class="sxs-lookup"><span data-stu-id="d99fc-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```  
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="d99fc-138">Assemblies do .NET framework, como mscorlib e System. dll não possuem ser adicionado à lista de confiança total porque eles são carregados como totalmente confiável de cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="d99fc-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3.  <span data-ttu-id="d99fc-139">Inicializar o <xref:System.AppDomainSetup> parâmetro o <xref:System.AppDomain.CreateDomain%2A> método.</span><span class="sxs-lookup"><span data-stu-id="d99fc-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="d99fc-140">Com esse parâmetro, você pode controlar muitas das configurações do novo <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="d99fc-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="d99fc-141">O <xref:System.AppDomainSetup.ApplicationBase%2A> propriedade é uma configuração importante e deve ser diferente de <xref:System.AppDomainSetup.ApplicationBase%2A> propriedade para o <xref:System.AppDomain> do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="d99fc-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="d99fc-142">Se o <xref:System.AppDomainSetup.ApplicationBase%2A> configurações são as mesmas, o aplicativo de confiança parcial pode obter o aplicativo de hospedagem exceção define, assim, a exploração de carga (como totalmente confiável).</span><span class="sxs-lookup"><span data-stu-id="d99fc-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="d99fc-143">Essa é outra razão por que não é recomendável um catch (exception).</span><span class="sxs-lookup"><span data-stu-id="d99fc-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="d99fc-144">Configurando o aplicativo base do host de forma diferente da base do aplicativo do aplicativo em modo seguro reduz o risco de explorações.</span><span class="sxs-lookup"><span data-stu-id="d99fc-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```  
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4.  <span data-ttu-id="d99fc-145">Chamar o <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> sobrecarga do método para criar o domínio de aplicativo usando os parâmetros que especificou.</span><span class="sxs-lookup"><span data-stu-id="d99fc-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="d99fc-146">A assinatura para este método é:</span><span class="sxs-lookup"><span data-stu-id="d99fc-146">The signature for this method is:</span></span>  
  
    ```  
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="d99fc-147">Informações adicionais:</span><span class="sxs-lookup"><span data-stu-id="d99fc-147">Additional information:</span></span>  
  
    -   <span data-ttu-id="d99fc-148">Isso é a única sobrecarga do <xref:System.AppDomain.CreateDomain%2A> método que utiliza um <xref:System.Security.PermissionSet> como um parâmetro e, portanto, a sobrecarga única que permite carregam um aplicativo em uma configuração de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="d99fc-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    -   <span data-ttu-id="d99fc-149">O `evidence` parâmetro não é usado para calcular um conjunto de permissões; ele é usado para identificação por outros recursos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d99fc-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    -   <span data-ttu-id="d99fc-150">Definindo o <xref:System.AppDomainSetup.ApplicationBase%2A> propriedade o `info` parâmetro é obrigatório para essa sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="d99fc-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    -   <span data-ttu-id="d99fc-151">O `fullTrustAssemblies` parâmetro tem o `params` palavra-chave, o que significa que não é necessário criar um <xref:System.Security.Policy.StrongName> matriz.</span><span class="sxs-lookup"><span data-stu-id="d99fc-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="d99fc-152">É permitido passar 0, 1 ou mais nomes fortes como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d99fc-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    -   <span data-ttu-id="d99fc-153">O código para criar o domínio de aplicativo é:</span><span class="sxs-lookup"><span data-stu-id="d99fc-153">The code to create the application domain is:</span></span>  
  
    ```  
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5.  <span data-ttu-id="d99fc-154">Carregar o código para a área restrita <xref:System.AppDomain> que você criou.</span><span class="sxs-lookup"><span data-stu-id="d99fc-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="d99fc-155">Isso pode ser feito de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="d99fc-155">This can be done in two ways:</span></span>  
  
    -   <span data-ttu-id="d99fc-156">Chamar o <xref:System.AppDomain.ExecuteAssembly%2A> método para o assembly.</span><span class="sxs-lookup"><span data-stu-id="d99fc-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    -   <span data-ttu-id="d99fc-157">Use o <xref:System.Activator.CreateInstanceFrom%2A> método para criar uma instância de uma classe derivada de <xref:System.MarshalByRefObject> no novo <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="d99fc-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="d99fc-158">O segundo método é preferível, pois ele torna mais fácil passar parâmetros para o novo <xref:System.AppDomain> instância.</span><span class="sxs-lookup"><span data-stu-id="d99fc-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="d99fc-159">O <xref:System.Activator.CreateInstanceFrom%2A> método fornece dois recursos importantes:</span><span class="sxs-lookup"><span data-stu-id="d99fc-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    -   <span data-ttu-id="d99fc-160">Você pode usar uma base de código que aponta para um local que não contém o assembly.</span><span class="sxs-lookup"><span data-stu-id="d99fc-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    -   <span data-ttu-id="d99fc-161">Você pode fazer a criação em um <xref:System.Security.CodeAccessPermission.Assert%2A> para confiança total (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), que permite que você crie uma instância de uma classe crítica.</span><span class="sxs-lookup"><span data-stu-id="d99fc-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="d99fc-162">(Isso ocorre sempre que o assembly tem sem marcações de transparência e é carregado como totalmente confiável). Portanto, você precisa ter cuidado para criar somente o código que você confia com essa função, e é recomendável que você crie apenas instâncias de classes totalmente confiáveis no novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d99fc-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```  
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="d99fc-163">Observe que, para criar uma instância de uma classe em um novo domínio, a classe tem que estender o <xref:System.MarshalByRefObject> classe</span><span class="sxs-lookup"><span data-stu-id="d99fc-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```  
    class Sandboxer:MarshalByRefObject  
    ```  
  
6.  <span data-ttu-id="d99fc-164">Decodificar a nova instância de domínio em uma referência neste domínio.</span><span class="sxs-lookup"><span data-stu-id="d99fc-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="d99fc-165">Esta referência é usada para executar o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="d99fc-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```  
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7.  <span data-ttu-id="d99fc-166">Chamar o `ExecuteUntrustedCode` método na instância do `Sandboxer` classe que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="d99fc-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```  
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="d99fc-167">Esta chamada é executada no domínio de aplicativo em modo seguro, que tem permissões restritas.</span><span class="sxs-lookup"><span data-stu-id="d99fc-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```  
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
                (new PermissionSet(PermissionState.Unrestricted)).Assert();  
                Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
    CodeAccessPermission.RevertAssert();  
                Console.ReadLine();  
            }  
        }  
    ```  
  
     <span data-ttu-id="d99fc-168"><xref:System.Reflection> é usado para obter um identificador de um método no assembly parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="d99fc-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="d99fc-169">O identificador pode ser usado para executar código em um modo seguro com permissões mínimas.</span><span class="sxs-lookup"><span data-stu-id="d99fc-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="d99fc-170">No código anterior, observe o <xref:System.Security.PermissionSet.Assert%2A> para a permissão de confiança total antes de imprimir o <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="d99fc-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```  
    new PermissionSet(PermissionState.Unrestricted)).Assert()  
    ```  
  
     <span data-ttu-id="d99fc-171">A declaração de confiança total é usada para obter informações estendidas do <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="d99fc-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="d99fc-172">Sem o <xref:System.Security.PermissionSet.Assert%2A>, o <xref:System.Security.SecurityException.ToString%2A> método <xref:System.Security.SecurityException> vai descobrir que há código parcialmente confiável na pilha e restringirá as informações retornadas.</span><span class="sxs-lookup"><span data-stu-id="d99fc-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="d99fc-173">Isso pode causar problemas de segurança se o código de confiança parcial foi possível ler essas informações, mas o risco é reduzido ao não conceder <xref:System.Security.Permissions.UIPermission>.</span><span class="sxs-lookup"><span data-stu-id="d99fc-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="d99fc-174">A declaração de confiança total deve ser usada com moderação e somente quando você tiver certeza de que você não permitem o código de confiança parcial elevar a confiança total.</span><span class="sxs-lookup"><span data-stu-id="d99fc-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="d99fc-175">Como regra, não chame código que não confiar na mesma função, e depois você chamou uma declaração de confiança total.</span><span class="sxs-lookup"><span data-stu-id="d99fc-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="d99fc-176">É recomendável sempre reverter assert quando tiver terminado de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="d99fc-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d99fc-177">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d99fc-177">Example</span></span>  
 <span data-ttu-id="d99fc-178">O exemplo a seguir implementa o procedimento na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="d99fc-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="d99fc-179">No exemplo, um projeto chamado `Sandboxer` um Visual Studio solução também contém um projeto chamado `UntrustedCode`, que implementa a classe `UntrustedClass`.</span><span class="sxs-lookup"><span data-stu-id="d99fc-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="d99fc-180">Este cenário pressupõe que você baixou um assembly de biblioteca que contém um método que deve retornar `true` ou `false` para indicar se o número fornecido é um número Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="d99fc-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="d99fc-181">Em vez disso, o método tenta ler um arquivo do seu computador.</span><span class="sxs-lookup"><span data-stu-id="d99fc-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="d99fc-182">O exemplo a seguir mostra o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="d99fc-182">The following example shows the untrusted code.</span></span>  
  
```  
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
  
 <span data-ttu-id="d99fc-183">A exemplo a seguir mostra o `Sandboxer` código do aplicativo que executa o código não confiável.</span><span class="sxs-lookup"><span data-stu-id="d99fc-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```  
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
            (new PermissionSet(PermissionState.Unrestricted)).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d99fc-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d99fc-184">See Also</span></span>  
 [<span data-ttu-id="d99fc-185">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="d99fc-185">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
