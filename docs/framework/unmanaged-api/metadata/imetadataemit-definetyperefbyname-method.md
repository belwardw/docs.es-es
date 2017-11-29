---
title: "IMetaDataEmit::DefineTypeRefByName (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeRefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ce04733fa9f149f155d850c53b65b263943cf8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="5e091-102">IMetaDataEmit::DefineTypeRefByName (Método)</span><span class="sxs-lookup"><span data-stu-id="5e091-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="5e091-103">Obtiene metadatos de un token para un tipo que se define en el ámbito especificado, que se encuentra fuera del ámbito actual.</span><span class="sxs-lookup"><span data-stu-id="5e091-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e091-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5e091-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e091-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5e091-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="5e091-106">[in] El token de especificar el ámbito de resolución.</span><span class="sxs-lookup"><span data-stu-id="5e091-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="5e091-107">Los siguientes tipos de token son válidos:</span><span class="sxs-lookup"><span data-stu-id="5e091-107">The following token types are valid:</span></span>  
  
-   <span data-ttu-id="5e091-108">`mdModuleRef`, si el tipo se define en el mismo ensamblado en el que se define el llamador.</span><span class="sxs-lookup"><span data-stu-id="5e091-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="5e091-109">`mdAssemblyRef`, si el tipo se define en un ensamblado distinto de aquél en el que se define el llamador.</span><span class="sxs-lookup"><span data-stu-id="5e091-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="5e091-110">`mdTypeRef`, si el tipo es un tipo anidado.</span><span class="sxs-lookup"><span data-stu-id="5e091-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
-   <span data-ttu-id="5e091-111">`mdModule`, si el tipo se define en el mismo módulo donde se define el llamador.</span><span class="sxs-lookup"><span data-stu-id="5e091-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="5e091-112">Es null, si el tipo está definido globalmente.</span><span class="sxs-lookup"><span data-stu-id="5e091-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="5e091-113">[in] El nombre del tipo de destino en Unicode.</span><span class="sxs-lookup"><span data-stu-id="5e091-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="5e091-114">[out] Un puntero a la `mdTypeRef` símbolo (token) que se asigna al tipo.</span><span class="sxs-lookup"><span data-stu-id="5e091-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e091-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e091-115">Requirements</span></span>  
 <span data-ttu-id="5e091-116">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e091-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e091-117">**Encabezado:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5e091-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e091-118">**Biblioteca:** usada como recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e091-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e091-119">**Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e091-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e091-120">Vea también</span><span class="sxs-lookup"><span data-stu-id="5e091-120">See Also</span></span>  
 [<span data-ttu-id="5e091-121">IMetaDataEmit (interfaz)</span><span class="sxs-lookup"><span data-stu-id="5e091-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="5e091-122">IMetaDataEmit2 (interfaz)</span><span class="sxs-lookup"><span data-stu-id="5e091-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)