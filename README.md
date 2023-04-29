# Unity_BillboardShader

<img src="https://github.com/XJINE/Unity_BillboardShader/blob/main/Screenshot.gif" width="100%" height="auto" />

These quads always show their faces to the camera.

```hlsl
v2f vert (appdata_full v)
{
	v2f o;

	float3 vpos       = mul(unity_ObjectToWorld, v.vertex.xyz);
	float4 worldCoord = float4(unity_ObjectToWorld._m03_m13_m23, 1);
	float4 viewPos    = mul(UNITY_MATRIX_V, worldCoord) + float4(vpos, 0);

	o.vertex = mul(UNITY_MATRIX_P, viewPos);
	o.uv     = v.texcoord;

	return o;
}
```