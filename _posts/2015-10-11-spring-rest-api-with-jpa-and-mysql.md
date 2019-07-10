---
title: Spring REST API with JPA and MySQL
---

Problem of saving nested objects in JPA and relation DB(MySQL)
For instance there is some request for API in json format:


    {
    "title" : "Address",
    "description" : "Address for remote access",
    "location" : "Bezrucova",
    "tier" : "2",
    "parameters" : [ {
        "name" : "name123",
        "value" : "123"
    } ]
    }



Object has set of another objects named "parameters".

So in code parameters defined like following in root class Record:

    @OneToMany(cascade = {CascadeType.ALL,CascadeType.PERSIST,CascadeType.MERGE}, mappedBy = "record")
        public Set<Parameter> parameters = new HashSet<>();


And following annotation is for child objects:


    @ManyToOne(fetch = FetchType.EAGER)
        @JoinColumn(name="record_id")
        private Record record;


Problem here, that in this case service would save only root object, ignoring parameters list. To prevent that and adjust expected behavior two more annotations must be add: one for root object, one for nested.

So final set of annotations for Record will look like that:


    @JsonManagedReference
        @OneToMany(cascade = {CascadeType.ALL,CascadeType.PERSIST,CascadeType.MERGE}, mappedBy = "record")
        public Set<Parameter> parameters = new HashSet<>();


For nested like that:

    @JsonBackReference
        @ManyToOne(fetch = FetchType.EAGER)
        @JoinColumn(name="record_id")
        private Record record;


