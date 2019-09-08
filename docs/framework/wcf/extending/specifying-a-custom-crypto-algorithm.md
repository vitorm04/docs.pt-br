---
title: Especificando um algoritmo de criptografia personalizada
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: cf4b3da82087a6daade9d6b939f3e1aac628cb01
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796895"
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Especificando um algoritmo de criptografia personalizada
O WCF permite que você especifique um algoritmo de criptografia personalizado a ser usado ao criptografar dados ou computação de assinaturas digitais. Isso é feito pelas seguintes etapas:  
  
1. Derive uma classe de<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2. Registrar o algoritmo  
  
3. Configure a associação com a <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>classe derivada.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>Derive uma classe de SecurityAlgorithmSuite  
 O <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> é uma classe base abstrata que permite que você especifique o algoritmo a ser usado ao executar várias operações relacionadas à segurança. Por exemplo, computar um hash para uma assinatura digital ou criptografar uma mensagem. O código a seguir mostra como derivar uma classe <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>de:  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a>Registrar o algoritmo personalizado  
 O registro pode ser feito em um arquivo de configuração ou em código imperativo. O registro de um algoritmo personalizado é feito criando-se um mapeamento entre uma classe que implementa um provedor de serviços de criptografia e um alias. O alias é então mapeado para um URI que é usado ao especificar o algoritmo na associação do serviço WCF. O seguinte trecho de configuração ilustra como registrar um algoritmo personalizado na configuração:  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 A seção sob o <`cryptoClasses`elemento > cria o mapeamento entre o SHA256CryptoServiceProvider e o alias "SHA256CSP". O elemento`nameEntry`< > cria o mapeamento entre o alias "SHA256CSP" e a URL especificada (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).  
  
 Para registrar o algoritmo personalizado no código, use <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> o método. Esse método cria os dois mapeamentos. O exemplo a seguir mostra como chamar esse método:  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Configurar a associação  
 Você configura a associação especificando a classe derivada <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>personalizada nas configurações de associação, conforme mostrado no trecho de código a seguir:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Para obter um exemplo de código completo, consulte a [agilidade de criptografia no](../samples/cryptographic-agility-in-wcf-security.md) exemplo de segurança do WCF.  
  
## <a name="see-also"></a>Consulte também

- [Protegendo serviços e clientes](../feature-details/securing-services-and-clients.md)
- [Protegendo serviços](../securing-services.md)
- [Visão geral de segurança](../feature-details/security-overview.md)
- [Conceitos de segurança](../feature-details/security-concepts.md)
