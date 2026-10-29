import Destination from "../models/Destination.js";

// 1. Distinct method
export const getDistinctLocations = async (req, res) => {
    const locations = await Destination.distinct("location");
    res.status(200).json(locations);
};

// 2. CountDocuments method
export const countDestinations = async (req, res) => {
    const count = await Destination.countDocuments();
    res.status(200).json({ totalDestinations: count });
};

// 3. Sort method
export const getSortedDestinations = async (req, res) => {
    const destinations = await Destination.find().sort({ price: 1 });
    res.status(200).json(destinations);
};

// 4. Limit method
export const getLimitedDestinations = async (req, res) => {
    const destinations = await Destination.find().limit(3);
    res.status(200).json(destinations);
};

// 5. Find destination by ID
export const showDestinationById = async (req, res) => {
    const destination = await Destination.findById(req.params.id);
    res.status(200).json(destination);
};

// 6. Create destination
export const createDestination = async (req, res) => {
    const destination = await Destination.create(req.body);
    res.status(201).json(destination);
};

// 7. FindByIdAndUpdate
export const updateDestinationById = async (req, res) => {
    const destination = await Destination.findByIdAndUpdate(
        req.params.id,
        { $set: req.body },
        { new: true, runValidators: true }
    );
    res.status(200).json(destination);
};

// 8. FindOneAndUpdate
export const updateDestination = async (req, res) => {
    const destination = await Destination.findOneAndUpdate(
        { name: req.params.name },
        { $set: req.body },
        { new: true, runValidators: true }
    );
    res.status(200).json(destination);
};

// 9. FindByIdAndDelete
export const deleteDestinationById = async (req, res) => {
    const destination = await Destination.findByIdAndDelete(
        req.params.id
    );
    res.status(200).json(destination);
};

// 10. FindOneAndDelete
export const deleteDestination = async (req, res) => {
    const destination = await Destination.findOneAndDelete({
        name: req.params.name
    });
    res.status(200).json(destination);
};
