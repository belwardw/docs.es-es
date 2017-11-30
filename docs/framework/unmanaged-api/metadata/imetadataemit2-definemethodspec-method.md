---
title: "IMetaDataEmit2::DefineMethodSpec (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.DefineMethodSpec
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 036654c733dc73d40c526bf5cad4dd3750e2e9d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="22df7-102">IMetaDataEmit2::DefineMethodSpec (Método)</span><span class="sxs-lookup"><span data-stu-id="22df7-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="22df7-103">Crea una instancia de un método genérica y obtiene un símbolo (token) a la definición.</span><span class="sxs-lookup"><span data-stu-id="22df7-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22df7-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="22df7-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22df7-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="22df7-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="22df7-106">[in] Un token para el método de la que se va a crear la instancia genérica.</span><span class="sxs-lookup"><span data-stu-id="22df7-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="22df7-107">El token debe ser de tipo `mdMethodDef` o `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="22df7-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="22df7-108">[in] Un puntero a la firma COM + binaria del método.</span><span class="sxs-lookup"><span data-stu-id="22df7-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="22df7-109">[in] El tamaño, en bytes, de `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="22df7-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="22df7-110">[out] Un token a la definición de la firma de metadatos del método.</span><span class="sxs-lookup"><span data-stu-id="22df7-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22df7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22df7-111">Requirements</span></span>  
 <span data-ttu-id="22df7-112">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22df7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22df7-113">**Encabezado:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="22df7-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22df7-114">**Biblioteca:** usada como recurso en MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22df7-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22df7-115">**Versiones de .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22df7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22df7-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="22df7-116">See Also</span></span>  
 [<span data-ttu-id="22df7-117">IMetaDataEmit2 (interfaz)</span><span class="sxs-lookup"><span data-stu-id="22df7-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="22df7-118">IMetaDataEmit (interfaz)</span><span class="sxs-lookup"><span data-stu-id="22df7-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)