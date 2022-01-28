db.people.insertOne({first_name: "Steven", last_name: "Top", email: "stop@gmail", gender: "Male", state: "MI", children: []});
db.people.insertOne({first_name: "Steven", last_name: "Top", email: "stop@gmail", gender: "Male", state: "MI", children: [{name: "Beth", age: 5,}]});
db.people.updateOne({first_name: "Clarence"}, {$set: {state: "South Dakota"}});
db.people.updateOne({first_name: "Rebecca", last_name: "Hayes"}, {$unset: {email: ""}});
db.people.updateMany({state: "Missouri"}, {$inc: {age: 1}});
db.people.updateOne({first_name: "Jerry", last_name: "Baker"}, {$set: {first_name: "Jerry", last_name: "Baker-Mendez", email: "jerry@classic.ly", gender:"Male", age: 28, state: "Vermont", "children": [{name: "Alan", age: 18}, {name: "Jenny", age: 3}] }});
db.people.deleteOne({_id: ObjectId("61f369b28d310004a8b7c0af")});
db.people.deleteMany({email: null});
db.submissions.insertMany([{title: "The River Bend", upvotes: 10, downvotes: 2, artist: ObjectId("61f369b28d310004a8b7c058")}, {title: "Nine Lives", upvotes: 7, downvotes: 0, artist: ObjectId("61f369b28d310004a8b7c086")}, {title: "Star Bright", upvotes: 19, downvotes: 3, artist: ObjectId("61f369b28d310004a8b7c109")}, {title: "Why Like This?", upvotes: 1, downvotes: 5, artist: ObjectId("61f369b28d310004a8b7c08f")}, {title: "Non Sequitur", upvotes: 11, downvotes: 1, artist: ObjectId("61f369b28d310004a8b7c056")}]);
db.submissions.updateOne({title: "The River Bend"}, { $inc: {upvotes: 2}});
db.submissions.updateMany({upvotes: {$gt: 10}}, {$set: {"round2": true}});
EXTENDED CHALLENGES
db.people.updateOne({_id: ObjectId("61f369b28d310004a8b7c114")}, {$push: {children: {name: "Melanie", age: 0}}});
db.people.updateOne({_id: ObjectId("61f369b28d310004a8b7c10d")}, {$set: {"children.3.name": "Cat"}, $inc: {"children.3.age": 1}});
db.submissions.find({$expr:{$gt:["$downvotes", "$upvotes"]}});