# Neat.TankerKoenig

Wrapper for TankerKoenig API. Get German gas prices around a region.
https://creativecommons.tankerkoenig.de/?page=info

```c#
var client = new TankerKoenigClient();
var stations = await client.GetAsync(
	string apikey,
	double latitude,
	double longitude,
	double radius = 25,
	Sort sort = Sort.Distance,
	Type type = Type.All);
```

Parameters:
```c#
public enum Sort
{
	Distance, //dist
	Price //price
}

public enum Type
{
	All,
	E5,
	E10,
	Diesel,
}
```

Result - List<Station>:

```c#
public class Station
{
	public string Id { get; set; }
	public string Name { get; set; }
	public string Brand { get; set; }
	public string Street { get; set; }
	public string Place { get; set; }
	[JsonProperty("lat")] public double Latitude { get; set; }
	[JsonProperty("lng")] public double Longitude { get; set; }
	[JsonProperty("dist")] public double Distance { get; set; }
	public decimal Diesel { get; set; }
	public decimal E5 { get; set; }
	public decimal E10 { get; set; }
	public bool IsOpen { get; set; }
	public string HouseNumber { get; set; }
	public string PostCode { get; set; }
}
```