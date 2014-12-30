```ruby
(100..200).to_a.each do |id|
  json = JSON.load(open "http://104.131.62.238/venuedbs/#{id}.json")
  v = Venue.create(name: json["name"], phone: json["phone"], capacity: json["max_capacty"])
  v.latitude = json["lng"]
  v.longitude = json["log"]
 
  if v.save
    json["spaces"].each do |sp_hash|
      space = v.venue_spaces.create(
        name: sp_hash["name"],
        max_reception: sp_hash["reception"],
        max_banquet: sp_hash["banquet"],
        max_theater:  sp_hash["theater"],
        max_classroom: sp_hash["classroom"],
        max_boardroom: sp_hash["boardroom"],
      )
      space.height = sp_hash["height"]
      space.sqft   = sp_hash["size"]
     space.save
    end
  else
    p v.errors
  end
end
```
